---
title: O ficheiro de esquema do MOF para um serviço da web de OData da gestão de criação | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65fbac8b-07d0-4513-bc8d-79f1f389be0f
caps.latest.revision: 5
ms.openlocfilehash: 7aadee07b38d2e9d87c5f0c548d13a5cdad1939f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080769"
---
# <a name="authoring-the-mof-schema-file-for-a-management-odata-web-service"></a><span data-ttu-id="8fddb-102">Authoring the MOF schema file for a Management OData web service (Autorizar o ficheiro de esquema MOF para um serviço Web OData de Gestão)</span><span class="sxs-lookup"><span data-stu-id="8fddb-102">Authoring the MOF schema file for a Management OData web service</span></span>

<span data-ttu-id="8fddb-103">Definir os recursos que o serviço da web OData da gestão expõe através da criação de um ficheiro MOF que utilizado o esquema de recurso de público.</span><span class="sxs-lookup"><span data-stu-id="8fddb-103">You define the resources that your Management OData web service exposes by creating a MOF file that used the public resource schema.</span></span> <span data-ttu-id="8fddb-104">Cada recurso é definido como uma classe no arquivo e as propriedades são definidas como membros de classe.</span><span class="sxs-lookup"><span data-stu-id="8fddb-104">Each resource is defined as a class in the file, and properties are defined as class members.</span></span> <span data-ttu-id="8fddb-105">Para obter mais informações sobre o esquema utilizado no ficheiro MOF, consulte [público de recurso de esquema](./public-resource-schema.md).</span><span class="sxs-lookup"><span data-stu-id="8fddb-105">For more information about the schema used in the MOF file, see [Public Resource Schema](./public-resource-schema.md).</span></span>

## <a name="example-mof-file"></a><span data-ttu-id="8fddb-106">Exemplo de ficheiro MOF</span><span class="sxs-lookup"><span data-stu-id="8fddb-106">Example MOF file</span></span>

<span data-ttu-id="8fddb-107">O arquivo a seguir define os recursos de serviço e o processo.</span><span class="sxs-lookup"><span data-stu-id="8fddb-107">The following file defines Service and Process resources.</span></span> <span data-ttu-id="8fddb-108">Cada um destes recursos corresponde a um objeto que pode ser gerido por um conjunto de cmdlet do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8fddb-108">Each of these resources corresponds to an object that can be managed by a set of Windows PowerShell cmdlet.</span></span> <span data-ttu-id="8fddb-109">As propriedades correspondem aos parâmetros utilizados por esses cmdlets.</span><span class="sxs-lookup"><span data-stu-id="8fddb-109">The properties correspond to parameters used by those cmdlets.</span></span>

<span data-ttu-id="8fddb-110">Cada um dos dois recursos contém as propriedades de tipo complexo.</span><span class="sxs-lookup"><span data-stu-id="8fddb-110">Each of the two resources contains properties that are of complex type.</span></span> <span data-ttu-id="8fddb-111">Os tipos complexos são definidos como classes modificadas com o `ComplexType` qualificador.</span><span class="sxs-lookup"><span data-stu-id="8fddb-111">The complex types are defined as classes modified with the `ComplexType` qualifier.</span></span>

```csharp

class PswsTest_Service
{
    [Key]      String  ServiceName;
    [Required] String  DisplayName;
    [Required] String  MachineName;
    [Required] String  ServiceType;
    [Required, EmbeddedInstance("PswsTest_DependentService")] String ServicesDependentOn [];
    [Required] Boolean CanPauseAndContinue;
    [Required] Boolean CanShutdown;
    [Required] Boolean CanStop;
    [Required, Etag] String Status;
};

class PswsTest_Process
{
    [Key] SInt32 Id;
    [Required] SInt32 BasePriority;
    [Required, EmbeddedInstance("PowerShell_PSCredential")] String Credential;
    [Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
    [Required] SInt32 HandleCount;
    [Required] String MachineName;
    [Required] SInt32 MainWindowHandle;
    [Required] String MainWindowTitle;
    [Required] SInt32 NonpagedSystemMemorySize;
    [Required] SInt64 NonpagedSystemMemorySize64;
    [Required] SInt32 PagedMemorySize;
    [Required] SInt64 PagedMemorySize64;
    [Required] SInt32 PagedSystemMemorySize;
    [Required] SInt64 PagedSystemMemorySize64;
    [Required] SInt32 PeakPagedMemorySize;
    [Required] SInt64 PeakPagedMemorySize64;
    [Required] SInt32 PeakWorkingSet;
    [Required] SInt64 PeakWorkingSet64;
    [Required] SInt32 PeakVirtualMemorySize;
    [Required] SInt64 PeakVirtualMemorySize64;
    [Required] SInt32 PrivateMemorySize;
    [Required] SInt64 PrivateMemorySize64;
    [Required] String ProcessName;
    [Required] Boolean Responding;
    [Required] SInt32 SessionId;
    [Required, EmbeddedInstance("PswsTest_ProcessStartInfo")] String StartInfo;
    [Required] SInt32 VirtualMemorySize;
    [Required] SInt64 VirtualMemorySize64;
    [Required] Boolean EnableRaisingEvents;
    [Required] SInt32 WorkingSet;
    [Required] SInt64 WorkingSet64;
};

[ComplexType]
class PswsTest_DependentService
{
    String  ServiceName;
};

[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};

[ComplexType]
class PswsTest_ProcessStartInfo
{
    String Verb;
    String Arguments;
    Boolean CreateNoWindow;
    Boolean RedirectStandardInput;
    Boolean RedirectStandardOutput ;
    Boolean RedirectStandardError;
    [EmbeddedInstance("PswsTest_Encoding")] String StandardErrorEncoding;
    [EmbeddedInstance("PswsTest_Encoding")] String StandardOutputEncoding;
    Boolean UseShellExecute;
    String UserName ;
    [EmbeddedInstance("PswsTest_SecureString")] String Password;
    String Domain;
    Boolean LoadUserProfile;
    String FileName;
    String WorkingDirectory ;
    Boolean ErrorDialog ;
    SInt32 ErrorDialogParentHandle;
    String WindowStyle;
};

[ComplexType]
class PswsTest_FileVersionInfo
{
    String Comments;
    String CompanyName;
    SInt32 FileBuildPart;
    String FileDescription;
    sInt32 FileMajorPart;
    SInt32 FileMinorPart;
    String FileName;
    SInt32 FilePrivatePart;
    String FileVersion;
    String InternalName;
    Boolean IsDebug;
    Boolean IsPatched;
    Boolean IsPrivateBuild;
    Boolean IsPreRelease;
    Boolean IsSpecialBuild;
    String Language;
    String LegalCopyright;
    String LegalTrademarks;
    String OriginalFilename;
    String PrivateBuild;
    SInt32 ProductBuildPart;
    SInt32 ProductMajorPart;
    SInt32 ProductMinorPart;
    String ProductName;
    SInt32 ProductPrivatePart;
    String ProductVersion;
    String SpecialBuild;
};

[ComplexType]
class PswsTest_Encoding
{
    String BodyName;
    String EncodingName;
    String HeaderName;
    String WebName;
    SInt32 WindowsCodePage;
    Boolean IsBrowserDisplay;
    Boolean IsBrowserSave;
    Boolean IsMailNewsDisplay;
    Boolean IsMailNewsSave;
    Boolean IsSingleByte;
    [EmbeddedInstance("PswsTest_EncoderFallback")] String EncoderFallback;
    [EmbeddedInstance("PswsTest_DecoderFallback")] String DecoderFallback;
    Boolean IsReadOnly;
    SInt32 CodePage;
};

[ComplexType]
class PswsTest_EncoderFallback
{
    SInt32 MaxCharCount;
};

[ComplexType]
class PswsTest_DecoderFallback
{
    SInt32 MaxCharCount;
};

[ComplexType]
class PswsTest_SecureString
{
    SInt32 Length;
};

[ComplexType]
class PswsTest_ProcessThread
{
    SInt32 BasePriority;
    SInt32 CurrentPriority;
    SInt32 Id;
    SInt32 IdealProcessor;
    String PriorityLevel;
    SInt32 StartAddress;
    String ThreadState;
    String WaitReason;
    SInt32 ProcessorAffinity;
};

[ComplexType]
class PswsTest_Stream
{
    Boolean CanRead;
    Boolean CanSeek;
    Boolean CanTimeout;
    Boolean CanWrite;
    SInt64 Length;
    SInt64 Position;
    SInt32 ReadTimeout;
    SInt32 WriteTimeout;
};

```

## <a name="see-also"></a><span data-ttu-id="8fddb-112">Veja Também</span><span class="sxs-lookup"><span data-stu-id="8fddb-112">See Also</span></span>

[<span data-ttu-id="8fddb-113">Criação de um serviço da Web de OData de gestão</span><span class="sxs-lookup"><span data-stu-id="8fddb-113">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)

[<span data-ttu-id="8fddb-114">Esquema de recurso público</span><span class="sxs-lookup"><span data-stu-id="8fddb-114">Public Resource Schema</span></span>](./public-resource-schema.md)