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
ms.openlocfilehash: ece57a102851efe0198f8993b60dba8e0eae6dec
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634418"
---
# <a name="common-msbuild-project-properties"></a>一般 MSBuild 專案屬性

下表列出了在 Visual Studio 專案檔案中定義或包含在 MSBuild 提供的 *.target*檔中的常用屬性。

 Visual Studio 中的專案檔 (*.csproj*、*.vbproj*、*.vcxproj* 及其他) 包含 MSBuild XML 程式碼，該程式碼會在您使用 IDE 建置專案時執行。 專案通常會匯入一或多個 *.targets* 檔案，用於定義其建置流程。 如需詳細資訊，請參閱 [MSBuild .targets 檔案](../msbuild/msbuild-dot-targets-files.md)。

## <a name="list-of-common-properties-and-parameters"></a>通用屬性和參數的清單

| 屬性或參數名稱 | 描述 |
|------------------------------------| - |
| AdditionalLibPaths | 指定其他資料夾，編譯器會在這些資料夾中尋找參考組件。 |
| AddModules | 讓編譯器將所指定檔案的類型資訊全部提供給您正在編譯的專案。 這個屬性相當於 `/addModules` 編譯器參數。 |
| ALToolPath | 可以找到*AL.exe 的*路徑。 此屬性覆蓋*AL.exe*的當前版本，以啟用其他版本的使用。 |
| ApplicationIcon | 要傳遞給編譯器的 *.ico*圖示檔以作為 Win32 圖示進行嵌入。 這個屬性相當於 `/win32icon` 編譯器參數。 |
| ApplicationManifest | 指定檔案路徑，這個檔案用於產生外部使用者帳戶控制 (User Account Control，UAC) 資訊清單資訊。 僅適用于面向 Windows Vista 的視覺化工作室專案。<br /><br /> 大部分情況下，資訊清單是以內嵌方式存在。 但是，如果使用註冊免費 COM 或 ClickOnce 部署，則清單可以是與應用程式程式集一起安裝的外部檔。 如需詳細資訊，請參閱本主題中的 NoWin32Manifest 屬性。 |
| AssemblyOriginatorKeyFile | 指定檔案，用來簽署組件 (*.snk* 或 *.pfx*)，並傳遞至 [ResolveKeySource 工作](../msbuild/resolvekeysource-task.md)以產生用來簽署組件的實際金鑰。 |
| AssemblySearchPaths | 在建置階段參考組件解析期間搜尋的位置清單。 路徑出現在這個清單中的順序是有意義的，因為較早列出的路徑優先於較晚列出的路徑。 |
| AssemblyName | 專案建置之後，最後輸出組件的名稱。 |
| BaseAddress | 指定主要輸出組件的基底位址。 這個屬性相當於 `/baseaddress` 編譯器參數。 |
| BaseIntermediateOutputPath | 在其中建立所有組態特有中繼輸出資料夾的最上層資料夾。 預設值是 `obj\`。 下列程式碼為範例：`<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BaseOutputPath | 指定輸出檔的基底路徑。 如果已設置，MSBuild 將使用`OutputPath = $(BaseOutputPath)\$(Configuration)\`。 範例語法：`<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BuildInParallel | 一個布林值，指示在使用多 Proc MSBuild 時是並行生成還是並行清理專案引用。 預設值為 `true`，表示系統有多個核心或處理器時，專案將會平行建置。 |
| BuildProjectReferences | 一個布林值，指示專案引用是否由 MSBuild 生成。 `false`如果在 Visual Studio 整合式開發環境 （IDE） 中構建專案，則`true`自動設置為（否則）。 可以在命令列上指定 `-p:BuildProjectReferences=false` 以避免檢查參考的專案是否為最新。 |
| CleanFile | 做為「清除快取」使用之檔案的名稱。 清除快取是所產生檔案的清單，這些檔案將要在清除作業期間刪除。 建置流程會將這個檔案放入中繼輸出路徑。<br /><br /> 這個屬性只會指定檔案名稱，不包含路徑資訊。 |
| CodePage | 指定編譯過程中所有原始程式碼檔使用的字碼頁。 這個屬性相當於 `/codepage` 編譯器參數。 |
| CompilerResponseFile | 可傳遞至編譯器工作的選擇性回應檔。 |
| 組態 | 您要建置的組態，它會是 "Debug" 或是 "Release"。 |
| CscToolPath | *csc.exe*的路徑，C# 編譯器。 |
| CustomBeforeMicrosoftCommonTargets | 專案檔或 targets 檔的名稱，該檔案會在一般 targets 匯入之前自動匯入。 |
| DebugSymbols | 布林值，指出建置是否要產生符號。<br /><br /> 設置 **-p：調試符號=命令**行上的 false 禁用生成程式資料庫 *（.pdb*） 符號檔。 |
| DebugType | 定義您要產生的偵錯資訊層級。 有效值為 "full"、"pdbonly"、"portable"、"embedded" 和 "none"。 |
| DefineConstants | 定義條件式編譯器常數。 符號/值組會以分號分隔，並且使用下列語法指定：<br /><br /> *symbol1 = value1 ; symbol2 = value2*<br /><br /> 這個屬性相當於 `/define` 編譯器參數。 |
| DefineDebug | 布林值，指出您是否要定義 DEBUG 常數。 |
| DefineTrace | 布林值，指出您是否要定義 TRACE 常數。 |
| DelaySign | 布林值，指出您是否要延遲簽署組件，而不要完整簽署組件。 |
| 具決定性 | 布林值，指出編譯器是否應該針對相同的輸入產生相同的組件。 此參數對應於 *vbc.exe* 和 *csc.exe* 編譯器的 `/deterministic` 參數。 |
| DisabledWarnings | 隱藏指定的警告。 您只需要指定警告識別項的數值部分。 若有多個警告，則會以分號分隔。 此參數對應于`/nowarn`*vbc.exe*編譯器的開關。 |
| DisableFastUpToDateCheck | 僅適用于視覺工作室的布林值。 Visual Studio 生成管理器使用名為 FastUpToDateCheck 的過程來確定是否必須重建專案才能是最新的。 此過程比使用 MSBuild 來確定這一點要快。 設置"禁用 FastUpToDateCheck"`true`屬性，以便繞過 Visual Studio 生成管理器，並強制它使用 MSBuild 來確定專案是否是最新的。 |
| DocumentationFile | 產生為 XML 文件檔案之檔案的名稱。 這個名稱只包含檔案名稱，不包含路徑資訊。 |
| ErrorReport | 指定編譯器工作報告編譯器內部錯誤的方式。 有效值為 "prompt"、"send" 或 "none"。 這個屬性相當於 `/errorreport` 編譯器參數。 |
| ExcludeDeploymentUrl | 如果專案檔案包含以下任一元素，則[生成部署清單任務](../msbuild/generatedeploymentmanifest-task.md)向部署清單添加部署提供程式標記：<br /><br /> -   UpdateUrl<br />-   InstallUrl<br />-   PublishUrl<br /><br /> 不過，若使用 ExcludeDeploymentUrl，即使指定了上述任何 URL，仍可以防止將 deploymentProvider 標記加入至部署資訊清單。 若要防止加入該標記，請將下列屬性加入至您的專案檔：<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**注：** 排除部署Url 不會在視覺化工作室 IDE 中公開，只能通過手動編輯專案檔案進行設置。 設置此屬性不會影響視覺化工作室中的發佈;因此，在視覺化 Studio 中設置此屬性不會影響發佈。也就是說，部署提供程式標記仍將添加到 PublishUrl 指定的 URL 中。 |
| FileAlignment | 以位元組為單位，指定要對齊輸出檔案區段的位置。 有效的值為 512、1024、2048、4096、8192。 這個屬性相當於 `/filealignment` 編譯器參數。 |
| FrameworkPathOverride | 指定*mscorlib.dll*和*Microsoft.visualbasic.dll*的位置。 此參數等效于`/sdkpath`*vbc.exe*編譯器的開關。 |
| GenerateDocumentation | （C#，視覺基礎）一個布林參數，用於指示文檔是否由生成生成。 如果`true`生成生成文檔資訊並將其與生成任務創建的可執行檔或庫的名稱一起放入 *.xml*檔中。 |
| 生成完整路徑 | （C#）使用[-fullpath](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option)編譯器選項為輸出中的檔案名生成完整路徑。 |
| GenerateSerializationAssemblies | 指出 XML 序列化組件是否應該由 *SGen.exe* 產生，其可設為開啟、自動或關閉。 這個屬性僅適用於以 .NET Framework 為目標的組件。 若要產生適用於 .NET Standard 或 .NET Core 組件的 XML 序列化組件，請參考 *Microsoft.XmlSerializer.Generator* NuGet 套件。 |
| IntermediateOutputPath | 如果沒有指定路徑，則為衍生自 `BaseIntermediateOutputPath` 的完整中繼輸出路徑。 例如 *，\obj_調試\\*。 |
| KeyContainerName | 強式名稱金鑰容器的名稱。 |
| KeyOriginatorFile | 強式名稱金鑰檔的名稱。 |
| ModuleAssemblyName | 組件的名稱，編譯的模組將合併到該組件中。 這個屬性相當於 `/moduleassemblyname` 編譯器參數。 |
| MSBuildProjectExtensionsPath | 指定專案延伸模組的路徑位置。 根據預設，這會採用與 `BaseIntermediateOutputPath` 相同的值。 |
| NoLogo | 布林值，指出您是否要關閉編譯器標誌。 這個屬性相當於 `/nologo` 編譯器參數。 |
| NoStdLib | 布林值，指出是否要避免參考標準程式庫 (*mscorlib.dll*)。 預設值是 `false`。 |
| NoVBRuntimeReference | 一個布林值，指示視覺基本運行時 *（Microsoft.VisualBasic.dll*） 是否應作為引用包含在專案中。 |
| NoWin32Manifest | 布林值，指出使用者帳戶控制 (UAC) 資訊清單資訊是否將會內嵌於應用程式的可執行檔中。 僅適用于面向 Windows Vista 的視覺化工作室專案。 在使用 ClickOnce 和無註冊 COM 部署的專案中，將忽略此元素。 `False` (預設值) 會指定將使用者帳戶控制 (UAC) 資訊清單資訊內嵌於應用程式的可執行檔中。 `True` 則會指定不內嵌 UAC 資訊清單資訊。<br /><br /> 此屬性僅適用于面向 Windows Vista 的視覺化工作室專案。 在使用 ClickOnce 和無註冊 COM 部署的專案中，將忽略此屬性。<br /><br /> 僅當不希望 Visual Studio 在應用程式的可執行檔中嵌入任何清單資訊時，才應添加 NoWin32清單;此過程稱為*虛擬化*。 若要使用虛擬化，請連同 `<ApplicationManifest>` 一起設定 `<NoWin32Manifest>`，如下所示：<br /><br /> - 對於視覺化基礎專案，請`<ApplicationManifest>`刪除節點。 （在視覺化基本專案中，`<NoWin32Manifest>`當`<ApplicationManifest>`存在節點時，將忽略。<br />- 對於 C#`<ApplicationManifest>`專案`False`，`<NoWin32Manifest>`設置為`True`和 。 （在 C#`<ApplicationManifest>`專案中，`<NoWin32Manifest>`重寫 。<br /> 此屬性等效于`/nowin32manifest`*vbc.exe*的編譯器開關。 |
| 最佳化 | 布林值，設定為 `true` 時，會啟用編譯器最佳化。 這個屬性相當於 `/optimize` 編譯器參數。 |
| OptionCompare | 指定如何進行字串比較。 有效值為 "binary" 或 "text"。 此屬性等效于`/optioncompare`*vbc.exe*的編譯器開關。 |
| OptionExplicit | 布林值，設定為 `true` 時，需要在原始程式碼中明確宣告變數。 這個屬性相當於 `/optionexplicit` 編譯器參數。 |
| OptionInfer | 布林值，設定為 `true` 時，會啟用變數的類型推斷。 這個屬性相當於 `/optioninfer` 編譯器參數。 |
| OptionStrict | 布林值，設定為 `true` 時，會讓建置工作強制執行嚴格的類型語意來限制隱含類型轉換。 此屬性相當於 *vbc.exe* 編譯器的 `/optionstrict` 參數。 |
| 出迪爾 | 指示專案或解決方案的最終輸出位置。 構建解決方案時，OutDir 可用於在一個位置收集多個專案輸出。 此外，OutDir 包含在用於解析引用的程式集搜索路徑中。 例如 *，bin_調試*。 |
| OutputPath | 指定輸出目錄的路徑，該路徑相對於專案目錄，例如 *bin\Debug*。 |
| OutputType | 指定輸出檔的檔案格式。 這個參數的值可以是下列其中一個：<br /><br /> -   Library。 建立程式碼程式庫  (預設值)。<br />-   Exe。 建立主控台應用程式 (Console Application)。<br />-   Module。 建立模組。<br />-   Winexe。 建立 Windows 程式。<br /><br /> 此屬性相當於 *vbc.exe* 編譯器的 `/target` 參數。 |
| OverwriteReadOnlyFiles | 布林值，指出您要讓建置覆寫唯讀檔案或是觸發錯誤。 |
| PathMap | 指定如何將實體路徑對應到編譯器所輸出的來源路徑名稱。 此屬性相當於 *csc.exe* 編譯器的 `/pathmap` 參數。 |
| PdbFile | 您要發出之 *.pdb* 檔案的檔案名稱。 此屬性相當於 *csc.exe* 編譯器的 `/pdb` 參數。 |
| 平台 | 做為您建置目標的作業系統。 有效值為 "Any CPU"、"x86" 及 "x64"。 |
| ProcessorArchitecture | 解析組件參考時使用的處理器架構。 有效值為 "msil"、"x86"、"amd64" 或 "ia64"。 |
| ProduceOnlyReferenceAssembly | 布林值，指示編譯器只發出參考組件，而不發出已編譯的程式碼。 無法與 `ProduceReferenceAssembly` 搭配使用。  此屬性對應於 *vbc.exe* 和 *csc.exe* 編譯器的 `/refonly` 參數。 |
| ProduceReferenceAssembly | 布林值，設定為 `true` 時會產生目前組件的[參考組件](/dotnet/standard/assembly/reference-assemblies)。 使用這項功能時，`Deterministic` 應該是 `true`。 此屬性對應於 *vbc.exe* 和 *csc.exe* 編譯器的 `/refout` 參數。 |
| RemoveIntegerChecks | 布林值，指出是否要停用整數溢位錯誤檢查。 預設值是 `false`。 此屬性相當於 *vbc.exe* 編譯器的 `/removeintchecks` 參數。 |
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
| Satellite_Win32Resource | 將 Win32 資源 (*.res* 檔案) 插入附屬組件。 |
| SGenToolPath | 選擇性的工具路徑，指出目前版本的 *SGen.exe* 遭到覆寫時，取得 *SGen.exe* 的位置。 這個屬性僅適用於 .NET Framework。|
| SGenUseProxyTypes | 布林值，指出是否要由 *SGen.exe* 產生 Proxy 類型。 這只適用於 *GenerateSerializationAssemblies* 設定為開啟時，且只適用於 .NET Framework。<br /><br /> SGen 目標會使用這個屬性設定 UseProxyTypes 旗標。 這個屬性預設為 true，而且沒有 UI 可用來變更這個屬性。 若要產生非 WebService 類型的序列化組件，請先將這個屬性新增至專案檔並將它設定為 false，再匯入 *Microsoft.Common.Targets* 或 *C#/VB.targets*。 |
| StartupObject | 指定包含 Main 方法或 Sub Main 程序的類別或模組。 這個屬性相當於 `/main` 編譯器參數。 |
| SubsystemVersion | 指定所產生的可執行檔能夠使用的最低子系統版本。 這個屬性相當於 `/subsystemversion` 編譯器參數。 如需這個屬性之預設值的資訊，請參閱 [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) 或 [/subsystemversion (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option)。 |
| TargetCompactFramework | 執行您建置之應用程式所需的 .NET Compact Framework 版本。 指定這個屬性可讓您參考無法以其他方式參考的某些 Framework 組件。 |
| TargetFrameworkVersion | 執行您正在建置之應用程式所需的 .NET Framework 版本。 指定這個屬性可讓您參考無法以其他方式參考的某些 Framework 組件。 |
| TreatWarningsAsErrors | 布林值參數，如果為 `true`，表示會將所有警告視為錯誤。 這個參數 (Parameter) 相當於 `/nowarn` 編譯器參數 (Switch)。 |
| UseHostCompilerIfAvailable | 布林值參數，如果為 `true`，表示建置工作會使用同處理序 (In-Process) 編譯器物件 (如果有的話)。 此參數僅由 Visual Studio 使用。 |
| Utf8Output | 布林值參數，如果為 `true`，則會使用 UTF-8 編碼記錄編譯器輸出。 這個參數 (Parameter) 相當於 `/utf8Output` 編譯器參數 (Switch)。 |
| VbcToolPath | 選擇性路徑，指出目前的 *vbc.exe* 版本遭到覆寫時，*vbc.exe* 的另一個位置。 |
| VbcVerbosity | 指定視覺化基本編譯器輸出的詳細程度。 有效值為 "Quiet"、"Normal" (預設值) 或 "Verbose"。 |
| VisualStudioVersion | 指定考慮用於執行這個專案的 Visual Studio 版本。 如果沒有指定這個屬性，MSBuild 會將它設定為合理的預設值。<br /><br /> 這個屬性會在數種專案類型中用來指定組建所使用的一組目標。 如果專案的 `ToolsVersion` 設定為 4.0 (含) 以上，則會使用 `VisualStudioVersion` 指定要使用的子工具組。 如需詳細資訊，請參閱 [Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)。 |
| WarningsAsErrors | 指定要視為錯誤的警告清單。 這個參數 (Parameter) 相當於 `/warnaserror` 編譯器參數 (Switch)。 |
| WarningsNotAsErrors | 指定不要視為錯誤的警告清單。 這個參數 (Parameter) 相當於 `/warnaserror` 編譯器參數 (Switch)。 |
| Win32Manifest | 應內嵌於最終組件中的資訊清單檔案名稱。 這個參數 (Parameter) 相當於 `/win32Manifest` 編譯器參數 (Switch)。 |
| Win32Resource | 要內嵌於最終組件中的 Win32 資源檔案名稱。 這個參數 (Parameter) 相當於 `/win32resource` 編譯器參數 (Switch)。 |

## <a name="see-also"></a>另請參閱

- [常見 MS 生成專案項](../msbuild/common-msbuild-project-items.md)
