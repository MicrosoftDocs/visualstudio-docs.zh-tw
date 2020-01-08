---
title: 一般 MSBuild 專案屬性 | Microsoft Docs
ms.date: 01/18/2018
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- msbuild, common properties
- msbuild, project file properties
- ExcludeDeploymentUrl property
- project file properties (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2797e8b51bba0e71db07ec748d7a6813183250fb
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596186"
---
# <a name="common-msbuild-project-properties"></a>一般 MSBuild 專案屬性
下表列出 Visual Studio 專案檔中所定義或 MSBuild 提供的 *.targets* 檔案中所包含的最常用屬性。

 Visual Studio 中的專案檔 ( *.csproj*、 *.vbproj*、 *.vcxproj* 及其他) 包含 MSBuild XML 程式碼，該程式碼會在您使用 IDE 建置專案時執行。 專案通常會匯入一或多個 *.targets* 檔案，用於定義其建置流程。 如需詳細資訊，請參閱 [MSBuild .targets 檔案](../msbuild/msbuild-dot-targets-files.md)。

## <a name="list-of-common-properties-and-parameters"></a>通用屬性和參數的清單

| 屬性或參數名稱 | 描述 |
|------------------------------------| - |
| AdditionalLibPaths | 指定其他資料夾，編譯器會在這些資料夾中尋找參考組件。 |
| AddModules | 讓編譯器將所指定檔案的類型資訊全部提供給您正在編譯的專案。 這個屬性相當於 `/addModules` 編譯器參數。 |
| ALToolPath | 可以找到 *AL.exe* 的路徑。 此屬性會覆寫 *AL.exe* 的目前版本，以使用其他版本。 |
| ApplicationIcon | 傳遞至編譯器內嵌為 Win32 圖示的 *.ico* 圖示檔。 這個屬性相當於 `/win32icon` 編譯器參數。 |
| ApplicationManifest | 指定檔案路徑，這個檔案用於產生外部使用者帳戶控制 (User Account Control，UAC) 資訊清單資訊。 僅適用於目標為 [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] 的 Visual Studio 專案。<br /><br /> 大部分情況下，資訊清單是以內嵌方式存在。 不過，如果您使用免註冊的 COM 或 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署，那麼資訊清單就可能是隨應用程式組件一起安裝的外部檔案。 如需詳細資訊，請參閱本主題中的 NoWin32Manifest 屬性。 |
| AssemblyOriginatorKeyFile | 指定檔案，用來簽署組件 ( *.snk* 或 *.pfx*)，並傳遞至 [ResolveKeySource 工作](../msbuild/resolvekeysource-task.md)以產生用來簽署組件的實際金鑰。 |
| AssemblySearchPaths | 在建置階段參考組件解析期間搜尋的位置清單。 路徑出現在這個清單中的順序是有意義的，因為較早列出的路徑優先於較晚列出的路徑。 |
| AssemblyName | 專案建置之後，最後輸出組件的名稱。 |
| BaseAddress | 指定主要輸出組件的基底位址。 這個屬性相當於 `/baseaddress` 編譯器參數。 |
| BaseOutputPath | 指定輸出檔的基底路徑。 如果設定這個屬性，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 將會使用 `OutputPath = $(BaseOutputPath)\$(Configuration)\`。 範例語法：`<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BaseIntermediateOutputPath | 在其中建立所有組態特有中繼輸出資料夾的最上層資料夾。 預設值為 `obj\`。 下列程式碼為範例：`<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BuildInParallel | 布林值，指出使用多處理器 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 時，專案參考為平行建置或清除。 預設值為 `true`，表示系統有多個核心或處理器時，專案將會平行建置。 |
| BuildProjectReferences | 布林值，指出專案參考是否由 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 建置。 如果您要在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 整合式開發環境 (IDE) 中建置專案，會自動設定為 `false`，否則設定為 `true`。 可以在命令列上指定 `-p:BuildProjectReferences=false` 以避免檢查參考的專案是否為最新。 |
| CleanFile | 做為「清除快取」使用之檔案的名稱。 清除快取是所產生檔案的清單，這些檔案將要在清除作業期間刪除。 建置流程會將這個檔案放入中繼輸出路徑。<br /><br /> 這個屬性只會指定檔案名稱，不包含路徑資訊。 |
| CodePage | 指定編譯過程中所有原始程式碼檔使用的字碼頁。 這個屬性相當於 `/codepage` 編譯器參數。 |
| CompilerResponseFile | 可傳遞至編譯器工作的選擇性回應檔。 |
| 組態 | 您要建置的組態，它會是 "Debug" 或是 "Release"。 |
| CscToolPath | *csc.exe* ([!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 編譯器) 的路徑。 |
| CustomBeforeMicrosoftCommonTargets | 專案檔或 targets 檔的名稱，該檔案會在一般 targets 匯入之前自動匯入。 |
| DebugSymbols | 布林值，指出建置是否要產生符號。<br /><br /> 在命令列上設定 **-p:DebugSymbols=false** 時，會停用產生程式資料庫 ( *.pdb*) 符號檔。 |
| DebugType | 定義您要產生的偵錯資訊層級。 有效值為 "full"、"pdbonly"、"portable"、"embedded" 和 "none"。 |
| DefineConstants | 定義條件式編譯器常數。 符號/值組會以分號分隔，並且使用下列語法指定：<br /><br /> *symbol1 = value1 ; symbol2 = value2*<br /><br /> 這個屬性相當於 `/define` 編譯器參數。 |
| DefineDebug | 布林值，指出您是否要定義 DEBUG 常數。 |
| DefineTrace | 布林值，指出您是否要定義 TRACE 常數。 |
| DelaySign | 布林值，指出您是否要延遲簽署組件，而不要完整簽署組件。 |
| Deterministic | 布林值，指出編譯器是否應該針對相同的輸入產生相同的組件。 此參數對應於 *vbc.exe* 和 *csc.exe* 編譯器的 `/deterministic` 參數。 |
| DisabledWarnings | 隱藏指定的警告。 您只需要指定警告識別項的數值部分。 若有多個警告，則會以分號分隔。 此參數對應於 *vbc.exe* 編譯器的 `/nowarn` 參數。 |
| DisableFastUpToDateCheck | 僅適用於 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的布林值。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 組建管理程式會使用稱為 FastUpToDateCheck 的處理序，判斷是否必須重建專案使其成為最新版本。 使用這個處理序比使用 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 判斷的速度快。 將 DisableFastUpToDateCheck 屬性設為 `true`，可讓您略過 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 組建管理程式，並強制使用 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 判斷專案是否為最新版本。 |
| DocumentationFile | 產生為 XML 文件檔案之檔案的名稱。 這個名稱只包含檔案名稱，不包含路徑資訊。 |
| ErrorReport | 指定編譯器工作報告編譯器內部錯誤的方式。 有效值為 "prompt"、"send" 或 "none"。 這個屬性相當於 `/errorreport` 編譯器參數。 |
| ExcludeDeploymentUrl | 如果專案檔包含下列任何項目，[GenerateDeploymentManifest 工作](../msbuild/generatedeploymentmanifest-task.md)會將 deploymentProvider 標記新增至部署資訊清單：<br /><br /> -   UpdateUrl<br />-   InstallUrl<br />-   PublishUrl<br /><br /> 不過，若使用 ExcludeDeploymentUrl，即使指定了上述任何 URL，仍可以防止將 deploymentProvider 標記加入至部署資訊清單。 若要防止加入該標記，請將下列屬性加入至您的專案檔：<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**注意：** ExcludeDeploymentUrl 不會在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 中公開，只能透過手動編輯專案檔的方式設定。 設定這個屬性不會影響 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 內的發行作業，也就是說，deploymentProvider 標記仍會加入至 PublishUrl 所指定的 URL。 |
| FileAlignment | 以位元組為單位，指定要對齊輸出檔案區段的位置。 有效的值為 512、1024、2048、4096、8192。 這個屬性相當於 `/filealignment` 編譯器參數。 |
| FrameworkPathOverride | 指定 *mscorlib.dll* 和 *microsoft.visualbasic.dll* 的位置。 此參數 (Parameter) 相當於 *vbc.exe* 編譯器的 `/sdkpath` 參數 (Switch)。 |
| GenerateDocumentation | （C#，Visual Basic）布林值參數，指出組建是否產生檔。 如果為 `true`，則建置會產生文件資訊，並將該資訊連同建置工作所建立的可執行檔或程式庫的名稱放入 *.xml* 檔。 |
| GenerateSerializationAssemblies | 指出 XML 序列化組件是否應該由 *SGen.exe* 產生，其可設為開啟、自動或關閉。 這個屬性僅適用於以 .NET Framework 為目標的組件。 若要產生適用於 .NET Standard 或 .NET Core 組件的 XML 序列化組件，請參考 *Microsoft.XmlSerializer.Generator* NuGet 套件。 |
| IntermediateOutputPath | 如果沒有指定路徑，則為衍生自 `BaseIntermediateOutputPath` 的完整中繼輸出路徑。 例如，\\\obj\debug。 |
| KeyContainerName | 強式名稱金鑰容器的名稱。 |
| KeyOriginatorFile | 強式名稱金鑰檔的名稱。 |
| MSBuildProjectExtensionsPath | 指定專案延伸模組的路徑位置。 根據預設，這會採用與 `BaseIntermediateOutputPath` 相同的值。 |
| ModuleAssemblyName | 組件的名稱，編譯的模組將合併到該組件中。 這個屬性相當於 `/moduleassemblyname` 編譯器參數。 |
| NoLogo | 布林值，指出您是否要關閉編譯器標誌。 這個屬性相當於 `/nologo` 編譯器參數。 |
| NoStdLib | 布林值，指出是否要避免參考標準程式庫 (*mscorlib.dll*)。 預設值為 `false`。 |
| NoVBRuntimeReference | 布林值，指出是否應加入 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 執行階段 (*Microsoft.VisualBasic.dll*) 作為專案中的參考。 |
| NoWin32Manifest | 布林值，指出使用者帳戶控制 (UAC) 資訊清單資訊是否將會內嵌於應用程式的可執行檔中。 僅適用於目標為 [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] 的 Visual Studio 專案。 在使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 和免註冊的 COM 所部署的專案中，會忽略這個項目。 `False` (預設值) 會指定將使用者帳戶控制 (UAC) 資訊清單資訊內嵌於應用程式的可執行檔中。 `True` 則會指定不內嵌 UAC 資訊清單資訊。<br /><br /> 這個屬性僅適用於目標為 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的 [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] 專案。 在使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 和免註冊的 COM 所部署的專案中，會忽略這個屬性。<br /><br /> 您應該僅在不希望 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 於應用程式的可執行檔中內嵌任何資訊清單資訊時，才新增 NoWin32Manifest，這個流程稱為「虛擬化」。 若要使用虛擬化，請連同 `<ApplicationManifest>` 一起設定 `<NoWin32Manifest>`，如下所示：<br /><br /> -  若為 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 專案，請移除 `<ApplicationManifest>` 節點。 (在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 專案中，如果有 `<ApplicationManifest>` 節點存在，則會忽略 `<NoWin32Manifest>`)。<br />-  若為 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 專案，請將 `<ApplicationManifest>` 設定為 `False`，並將 `<NoWin32Manifest>` 設定為 `True`。 (在 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 專案中，`<ApplicationManifest>` 會覆寫 `<NoWin32Manifest>`)。<br /> 此屬性相當於 *vbc.exe* 的 `/nowin32manifest` 編譯器參數。 |
| Optimize | 布林值，設定為 `true` 時，會啟用編譯器最佳化。 這個屬性相當於 `/optimize` 編譯器參數。 |
| OptionCompare | 指定如何進行字串比較。 有效值為 "binary" 或 "text"。 此屬性相當於 *vbc.exe* 的 `/optioncompare` 編譯器參數。 |
| OptionExplicit | 布林值，設定為 `true` 時，需要在原始程式碼中明確宣告變數。 這個屬性相當於 `/optionexplicit` 編譯器參數。 |
| OptionInfer | 布林值，設定為 `true` 時，會啟用變數的類型推斷。 這個屬性相當於 `/optioninfer` 編譯器參數。 |
| OptionStrict | 布林值，設定為 `true` 時，會讓建置工作強制執行嚴格的類型語意來限制隱含類型轉換。 此屬性相當於 *vbc.exe* 編譯器的 `/optionstrict` 參數。 |
| OutputPath | 指定輸出目錄的路徑，該路徑相對於專案目錄，例如 *bin\Debug*。 |
| OutputType | 指定輸出檔的檔案格式。 這個參數的值可以是下列其中一個：<br /><br /> -   Library。 建立程式碼程式庫 (預設值)。<br />-   Exe。 建立主控台應用程式 (Console Application)。<br />-   Module。 建立模組。<br />-   Winexe。 建立 Windows 程式。<br /><br /> 此屬性相當於 *vbc.exe* 編譯器的 `/target` 參數。 |
| OverwriteReadOnlyFiles | 布林值，指出您要讓建置覆寫唯讀檔案或是觸發錯誤。 |
| PathMap | 指定如何將實體路徑對應到編譯器所輸出的來源路徑名稱。 此屬性相當於 *csc.exe* 編譯器的 `/pathmap` 參數。 |
| PdbFile | 您要發出之 *.pdb* 檔案的檔案名稱。 此屬性相當於 *csc.exe* 編譯器的 `/pdb` 參數。 |
| Platform | 做為您建置目標的作業系統。 有效值為 "Any CPU"、"x86" 及 "x64"。 |
| ProduceReferenceAssembly | 布林值，設定為 `true` 時會產生目前組件的[參考組件](/dotnet/standard/assembly/reference-assemblies)。 使用這項功能時，`Deterministic` 應該是 `true`。 此屬性對應於 *vbc.exe* 和 *csc.exe* 編譯器的 `/refout` 參數。 |
| ProduceOnlyReferenceAssembly | 布林值，指示編譯器只發出參考組件，而不發出已編譯的程式碼。 無法與 `ProduceReferenceAssembly` 搭配使用。  此屬性對應於 *vbc.exe* 和 *csc.exe* 編譯器的 `/refonly` 參數。 |
| RemoveIntegerChecks | 布林值，指出是否要停用整數溢位錯誤檢查。 預設值為 `false`。 此屬性相當於 *vbc.exe* 編譯器的 `/removeintchecks` 參數。 |
| SGenUseProxyTypes | 布林值，指出是否要由 *SGen.exe* 產生 Proxy 類型。 這只適用於 *GenerateSerializationAssemblies* 設定為開啟時，且只適用於 .NET Framework。<br /><br /> SGen 目標會使用這個屬性設定 UseProxyTypes 旗標。 這個屬性預設為 true，而且沒有 UI 可用來變更這個屬性。 若要產生非 WebService 類型的序列化組件，請先將這個屬性新增至專案檔並將它設定為 false，再匯入 *Microsoft.Common.Targets* 或 *C#/VB.targets*。 |
| SGenToolPath | 選擇性的工具路徑，指出目前版本的 *SGen.exe* 遭到覆寫時，取得 *SGen.exe* 的位置。 這個屬性僅適用於 .NET Framework。|
| StartupObject | 指定包含 Main 方法或 Sub Main 程序的類別或模組。 這個屬性相當於 `/main` 編譯器參數。 |
| ProcessorArchitecture | 解析組件參考時使用的處理器架構。 有效值為 "msil"、"x86"、"amd64" 或 "ia64"。 |
| RootNamespace | 命名內嵌資源時使用的根命名空間。 這個命名空間是內嵌資源資訊清單名稱的一部分。 |
| Satellite_AlgorithmId | 建立附屬組件時要使用之 *AL.exe* 雜湊演算法的 ID。 |
| Satellite_BaseAddress | 使用 `CreateSatelliteAssemblies` 目標建置文化特性特有的附屬組件時，要使用的基底位址。 |
| Satellite_CompanyName | 產生附屬組件期間要傳入 *AL.exe* 的公司名稱。 |
| Satellite_Configuration | 產生附屬組件期間要傳入 *AL.exe* 的組態名稱。 |
| Satellite_Description | 產生附屬組件期間要傳入 *AL.exe* 的描述文字。 |
| Satellite_EvidenceFile | 在資源名稱為 "Security.Evidence" 的附屬組件中內嵌指定的檔案。 |
| Satellite_FileVersion | 指定附屬組件中 [檔案版本] 欄位的字串。 |
| Satellite_Flags | 指定附屬組件中 [旗標] 欄位的值。 |
| Satellite_GenerateFullPaths | 設定讓建置工作針對錯誤訊息中報告的任何檔案使用絕對路徑。 |
| Satellite_LinkResource | 將指定的資源檔連結至附屬組件。 |
| Satellite_MainEntryPoint | 指定在產生附屬組件期間模組轉換成可執行檔時，用來做為進入點之方法的完整名稱 (也就是 class.method)。 |
| Satellite_ProductName | 指定附屬組件中 [產品] 欄位的字串。 |
| Satellite_ProductVersion | 指定附屬組件中 [ProductVersion] 欄位的字串。 |
| Satellite_TargetType | 將附屬組件輸出檔的檔案格式指定為 "library"、"exe" 或 "win"。 預設值為 "library"。 |
| Satellite_Title | 指定附屬組件中 [標題] 欄位的字串。 |
| Satellite_Trademark | 指定附屬組件中 [商標] 欄位的字串。 |
| Satellite_Version | 指定附屬組件的版本資訊。 |
| Satellite_Win32Icon | 將 *.ico* 圖示檔插入附屬組件。 |
| Satellite_Win32Resource | 將 Win32 資源 ( *.res* 檔案) 插入附屬組件。 |
| SubsystemVersion | 指定所產生的可執行檔能夠使用的最低子系統版本。 這個屬性相當於 `/subsystemversion` 編譯器參數。 如需這個屬性之預設值的資訊，請參閱 [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) 或 [/subsystemversion (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option)。 |
| TargetCompactFramework | 執行您建置之應用程式所需的 .NET Compact Framework 版本。 指定這個屬性可讓您參考無法以其他方式參考的某些 Framework 組件。 |
| TargetFrameworkVersion | 執行您正在建置之應用程式所需的 .NET Framework 版本。 指定這個屬性可讓您參考無法以其他方式參考的某些 Framework 組件。 |
| TreatWarningsAsErrors | 布林值參數，如果為 `true`，表示會將所有警告視為錯誤。 這個參數 (Parameter) 相當於 `/nowarn` 編譯器參數 (Switch)。 |
| UseHostCompilerIfAvailable | 布林值參數，如果為 `true`，表示建置工作會使用同處理序 (In-Process) 編譯器物件 (如果有的話)。 這個參數僅供 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 使用。 |
| Utf8Output | 布林值參數，如果為 `true`，則會使用 UTF-8 編碼記錄編譯器輸出。 這個參數 (Parameter) 相當於 `/utf8Output` 編譯器參數 (Switch)。 |
| VbcToolPath | 選擇性路徑，指出目前的 *vbc.exe* 版本遭到覆寫時，*vbc.exe* 的另一個位置。 |
| VbcVerbosity | 指定 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 編譯器輸出的詳細資訊。 有效值為 "Quiet"、"Normal" (預設值) 或 "Verbose"。 |
| VisualStudioVersion | 指定考慮用於執行這個專案的 Visual Studio 版本。 如果沒有指定這個屬性，MSBuild 會將它設定為合理的預設值。<br /><br /> 這個屬性會在數種專案類型中用來指定組建所使用的一組目標。 如果專案的 `ToolsVersion` 設定為 4.0 (含) 以上，則會使用 `VisualStudioVersion` 指定要使用的子工具組。 如需詳細資訊，請參閱 [Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)。 |
| WarningsAsErrors | 指定要視為錯誤的警告清單。 這個參數 (Parameter) 相當於 `/warnaserror` 編譯器參數 (Switch)。 |
| WarningsNotAsErrors | 指定不要視為錯誤的警告清單。 這個參數 (Parameter) 相當於 `/warnaserror` 編譯器參數 (Switch)。 |
| Win32Manifest | 應內嵌於最終組件中的資訊清單檔案名稱。 這個參數 (Parameter) 相當於 `/win32Manifest` 編譯器參數 (Switch)。 |
| Win32Resource | 要內嵌於最終組件中的 Win32 資源檔案名稱。 這個參數 (Parameter) 相當於 `/win32resource` 編譯器參數 (Switch)。 |

## <a name="see-also"></a>請參閱
- [通用的 MSBuild 專案項目](../msbuild/common-msbuild-project-items.md)
