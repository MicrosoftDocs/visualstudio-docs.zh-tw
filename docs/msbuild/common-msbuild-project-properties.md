---
title: 一般 MSBuild 專案屬性 | Microsoft Docs
description: 瞭解可在專案檔中定義或使用的一般 MSBuild 專案屬性，或是 MSBuild 提供的 .targets 檔案中所包含的屬性。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2622c5e86a22b4dc7ef9bf1fa3c426a588f40bab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851994"
---
# <a name="common-msbuild-project-properties"></a>一般 MSBuild 專案屬性

下表列出 Visual Studio 專案檔中所定義或 MSBuild 提供的 *.targets* 檔案中所包含的常用屬性。

 Visual Studio 中的專案檔 (*.csproj*、*.vbproj*、*.vcxproj* 及其他) 包含 MSBuild XML 程式碼，該程式碼會在您使用 IDE 建置專案時執行。 專案通常會匯入一或多個 *.targets* 檔案，用於定義其建置流程。 如需詳細資訊，請參閱 [MSBuild .targets 檔案](../msbuild/msbuild-dot-targets-files.md)。

## <a name="list-of-common-properties-and-parameters"></a>通用屬性和參數的清單

| 屬性或參數名稱 | 專案類型 | Description |
|------------------------------------| - | - |
| AdditionalLibPaths | .NET | 指定其他資料夾，編譯器會在這些資料夾中尋找參考組件。 |
| AddModules | .NET | 讓編譯器將所指定檔案的類型資訊全部提供給您正在編譯的專案。 這個屬性相當於 `/addModules` 編譯器參數。 |
| ALToolPath | .NET | 可以找到 *AL.exe* 的路徑。 這個屬性會覆寫目前的 *AL.exe* 版本，以允許使用不同的版本。 |
| ApplicationIcon | .NET | 要傳遞至編譯器以做為 Win32 圖示的 *.ico* 圖示檔。 這個屬性相當於 `/win32icon` 編譯器參數。 |
| ApplicationManifest | 全部 | 指定檔案路徑，這個檔案用於產生外部使用者帳戶控制 (User Account Control，UAC) 資訊清單資訊。 僅適用于以 Windows Vista 為目標的 Visual Studio 專案。<br /><br /> 大部分情況下，資訊清單是以內嵌方式存在。 但是，如果您使用免註冊的 COM 或 ClickOnce 部署，則資訊清單可以是與應用程式元件一起安裝的外部檔案。 如需詳細資訊，請參閱本主題中的 NoWin32Manifest 屬性。 |
| AssemblyOriginatorKeyFile | .NET | 指定檔案，用來簽署組件 (*.snk* 或 *.pfx*)，並傳遞至 [ResolveKeySource 工作](../msbuild/resolvekeysource-task.md)以產生用來簽署組件的實際金鑰。 |
| AssemblySearchPaths | .NET | 在建置階段參考組件解析期間搜尋的位置清單。 路徑出現在這個清單中的順序是有意義的，因為較早列出的路徑優先於較晚列出的路徑。 |
| AssemblyName | .NET | 專案建置之後，最後輸出組件的名稱。 |
| BaseAddress | .NET | 指定主要輸出組件的基底位址。 這個屬性相當於 `/baseaddress` 編譯器參數。 |
| BaseIntermediateOutputPath | 全部 | 在其中建立所有組態特有中繼輸出資料夾的最上層資料夾。 預設值是 `obj\`。 下列程式碼為範例：`<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BaseOutputPath | 全部 | 指定輸出檔的基底路徑。 如果設定，MSBuild 將會使用 `OutputPath = $(BaseOutputPath)\$(Configuration)\` 。 範例語法：`<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BuildInParallel | 全部 | 布林值，指出使用多處理器 MSBuild 時，是否平行建立或清除專案參考。 預設值為 `true`，表示系統有多個核心或處理器時，專案將會平行建置。 |
| BuildProjectReferences | 全部 | 指出專案參考是否由 MSBuild 建立的布林值。 `false`如果您要在 Visual Studio 整合式開發環境中建立專案，則會自動設為， (IDE) ， `true` 否則為。 可以在命令列上指定 `-p:BuildProjectReferences=false` 以避免檢查參考的專案是否為最新。 |
| CleanFile | 全部 | 做為「清除快取」使用之檔案的名稱。 清除快取是所產生檔案的清單，這些檔案將要在清除作業期間刪除。 建置流程會將這個檔案放入中繼輸出路徑。<br /><br /> 這個屬性只會指定檔案名稱，不包含路徑資訊。 |
| CodePage | .NET | 指定編譯過程中所有原始程式碼檔使用的字碼頁。 這個屬性相當於 `/codepage` 編譯器參數。 |
| CompilerResponseFile | .NET | 可傳遞至編譯器工作的選擇性回應檔。 |
| 組態 | 全部 | 您所建立的設定，通常是 `Debug` 或 `Release` ，但可在方案和專案層級進行設定。 |
| CscToolPath | C# | C # 編譯器 *csc.exe* 的路徑。 |
| CustomBeforeMicrosoftCommonTargets | 全部 | 專案檔或 targets 檔的名稱，該檔案會在一般 targets 匯入之前自動匯入。 |
| DebugSymbols | 全部 | 布林值，指出建置是否要產生符號。<br /><br /> 在命令列上設定 **-p:DebugSymbols = false** ，會停用產生程式資料庫 (*.pdb*) 符號檔。 |
| DebugType | 全部 | 定義您要產生的偵錯資訊層級。 有效值為 "full"、"pdbonly"、"portable"、"embedded" 和 "none"。 |
| DefineConstants | .NET | 定義條件式編譯器常數。 符號/值組會以分號分隔，並且使用下列語法指定：<br /><br /> *symbol1 = value1 ; symbol2 = value2*<br /><br /> 這個屬性相當於 `/define` 編譯器參數。 |
| DefineDebug | 全部 |  布林值，指出您是否要定義 DEBUG 常數。 |
| DefineTrace | 全部 | 布林值，指出您是否要定義 TRACE 常數。 |
| DelaySign | .NET | 布林值，指出您是否要延遲簽署組件，而不要完整簽署組件。 |
| 具決定性 | .NET | 布林值，指出編譯器是否應該針對相同的輸入產生相同的組件。 此參數對應于編譯器的參數 `/deterministic` 。 |
| DisableFastUpToDateCheck | 全部 | 僅適用于 Visual Studio 的布林值。 Visual Studio 組建管理員會使用稱為 FastUpToDateCheck 的程式，來判斷是否必須將專案重建為最新狀態。 此程式比使用 MSBuild 來判斷此程式更快。 將 Disablefastuptodatecheck 設屬性設定為可 `true` 讓您略過 Visual Studio 組建管理員，並強制它使用 MSBuild 判斷專案是否為最新狀態。 |
| DocumentationFile | .NET | 產生為 XML 文件檔案之檔案的名稱。 這個名稱只包含檔案名稱，不包含路徑資訊。 |
| ErrorReport | .NET | 指定編譯器工作報告編譯器內部錯誤的方式。 有效值為 "prompt"、"send" 或 "none"。 這個屬性相當於 `/errorreport` 編譯器參數。 |
| ExcludeDeploymentUrl | .NET | 如果專案檔包含下列任何專案， [GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md) 工作會將 deploymentProvider 標記加入至部署資訊清單：<br /><br /> -   UpdateUrl<br />-   InstallUrl<br />-   PublishUrl<br /><br /> 不過，若使用 ExcludeDeploymentUrl，即使指定了上述任何 URL，仍可以防止將 deploymentProvider 標記加入至部署資訊清單。 若要防止加入該標記，請將下列屬性加入至您的專案檔：<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**注意：**  ExcludeDeploymentUrl 不會在 Visual Studio IDE 中公開，而且只能透過手動編輯專案檔案來設定。 設定這個屬性不會影響 Visual Studio 內的發行;也就是說，deploymentProvider 標記仍會加入至 PublishUrl 所指定的 URL。 |
| FileAlignment | .NET | 以位元組為單位，指定要對齊輸出檔案區段的位置。 有效的值為 512、1024、2048、4096、8192。 這個屬性相當於 `/filealignment` 編譯器參數。 |
| FrameworkPathOverride | Visual Basic | 指定 *mscorlib.dll* 和 *microsoft.visualbasic.dll* 的位置。 此參數相當於 `/sdkpath` *vbc.exe* 編譯器的參數。 |
| GenerateDocumentation | .NET | 布林值參數，指出建置是否要產生文件。 如果 `true` 為，則組建會產生檔資訊，並將其放在 *.xml* 檔案中，並連同建立工作所建立的可執行檔或程式庫的名稱。 |
| GenerateFullPaths | C# | 使用 [-fullpaths](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option) 編譯器選項，在輸出中產生檔案名的完整路徑。 |
| GenerateSerializationAssemblies | .NET | 指出 XML 序列化組件是否應該由 *SGen.exe* 產生，其可設為開啟、自動或關閉。 這個屬性僅適用於以 .NET Framework 為目標的組件。 若要產生適用於 .NET Standard 或 .NET Core 組件的 XML 序列化組件，請參考 *Microsoft.XmlSerializer.Generator* NuGet 套件。 |
| IntermediateOutputPath | 全部 | 如果沒有指定路徑，則為衍生自 `BaseIntermediateOutputPath` 的完整中繼輸出路徑。 例如， *\obj\debug \\*。 |
| KeyContainerName | 全部 | 強式名稱金鑰容器的名稱。 |
| KeyOriginatorFile | 全部 | 強式名稱金鑰檔的名稱。 |
| ModuleAssemblyName | .NET | 組件的名稱，編譯的模組將合併到該組件中。 這個屬性相當於 `/moduleassemblyname` 編譯器參數。 |
| MSBuildProjectExtensionsPath | 全部 | 指定專案延伸模組的路徑位置。 根據預設，這會採用與 `BaseIntermediateOutputPath` 相同的值。 |
| NoLogo | 全部 | 布林值，指出您是否要關閉編譯器標誌。 這個屬性相當於 `/nologo` 編譯器參數。 |
| NoStdLib | .NET | 布林值，指出是否要避免參考標準程式庫 (*mscorlib.dll*)。 預設值是 `false`。 |
| NoVBRuntimeReference | Visual Basic | 布林值，指出 Visual Basic 執行時間 (*Microsoft.VisualBasic.dll*) 是否應包含為專案中的參考。 |
| NoWarn | .NET | 隱藏指定的警告。 您只需要指定警告識別項的數值部分。 若有多個警告，則會以分號分隔。 此參數對應于編譯器的參數 `/nowarn` 。 |
| NoWin32Manifest | .NET | 布林值，指出使用者帳戶控制 (UAC) 資訊清單資訊是否將會內嵌於應用程式的可執行檔中。 僅適用于以 Windows Vista 為目標的 Visual Studio 專案。 在使用 ClickOnce 和 Registration-Free COM 所部署的專案中，會忽略這個元素。 `False` (預設值) 會指定將使用者帳戶控制 (UAC) 資訊清單資訊內嵌於應用程式的可執行檔中。 `True` 則會指定不內嵌 UAC 資訊清單資訊。<br /><br /> 這個屬性只適用于以 Windows Vista 為目標 Visual Studio 專案。 在使用 ClickOnce 和 Registration-Free COM 所部署的專案中，會忽略這個屬性。<br /><br /> 只有當您不希望 Visual Studio 在應用程式的可執行檔中內嵌任何資訊清單資訊時，才應該新增 NoWin32Manifest;此程式稱為「 *虛擬化*」。 若要使用虛擬化，請連同 `<ApplicationManifest>` 一起設定 `<NoWin32Manifest>`，如下所示：<br /><br /> -針對 Visual Basic 專案，移除 `<ApplicationManifest>` 節點。 `<NoWin32Manifest>`當節點存在時，會忽略 Visual Basic 專案中的 (`<ApplicationManifest>` 。 ) <br />-若為 c # 專案，請將設定 `<ApplicationManifest>` 為，並將設定為 `False` `<NoWin32Manifest>` `True` 。 C # 專案中的 (， `<ApplicationManifest>` 覆寫 `<NoWin32Manifest>` 。 ) <br /> 這個屬性相當於vbc.exe的 `/nowin32manifest` 編譯器參數。  |
| 最佳化 | .NET | 布林值，設定為 `true` 時，會啟用編譯器最佳化。 這個屬性相當於 `/optimize` 編譯器參數。 |
| OptionCompare | VisualBasic | 指定如何進行字串比較。 有效值為 "binary" 或 "text"。 這個屬性相當於vbc.exe的 `/optioncompare` 編譯器參數。  |
| OptionExplicit | Visual Basic | 布林值，設定為 `true` 時，需要在原始程式碼中明確宣告變數。 這個屬性相當於 `/optionexplicit` 編譯器參數。 |
| OptionInfer | Visual Basic | 布林值，設定為 `true` 時，會啟用變數的類型推斷。 這個屬性相當於 `/optioninfer` 編譯器參數。 |
| OptionStrict | Visual Basic | 布林值，設定為 `true` 時，會讓建置工作強制執行嚴格的類型語意來限制隱含類型轉換。 此屬性相當於 *vbc.exe* 編譯器的 `/optionstrict` 參數。 |
| OutDir | 全部 | 表示專案或方案的最終輸出位置。 建立方案時，OutDir 可以用來在一個位置收集多個專案輸出。 此外，OutDir 也包含在用來解析參考的 AssemblySearchPaths 中。 例如， *bin\Debug*。 |
| OutputPath | 全部 | 指定輸出目錄的路徑，該路徑相對於專案目錄，例如 *bin\Debug*。 |
| OutputType | 全部 |  指定輸出檔的檔案格式。 這個參數的值可以是下列其中一個：<br /><br /> -   Library。 建立程式碼程式庫  (預設值)。<br />-   Exe。 建立主控台應用程式 (Console Application)。<br />-   Module。 建立模組。<br />-   Winexe。 建立 Windows 程式。<br /><br /> 針對 c # 和 Visual Basic，此屬性相當於 `/target` 參數。 |
| OverwriteReadOnlyFiles | 全部 | 布林值，指出您要讓建置覆寫唯讀檔案或是觸發錯誤。 |
| PathMap | .NET | 指定如何將實體路徑對應到編譯器所輸出的來源路徑名稱。 這個屬性就相當於 `/pathmap` 編譯器的參數。 |
| PdbFile | .NET | 您要發出之 *.pdb* 檔案的檔案名稱。 此屬性相當於 *csc.exe* 編譯器的 `/pdb` 參數。 |
| 平台 | 全部 | 做為您建置目標的作業系統。 .NET Framework 組建的範例包括「任何 CPU」、「x86」和「x64」。 |
| ProcessorArchitecture | .NET | 解析組件參考時使用的處理器架構。 有效值為 "msil"、"x86"、"amd64" 或 "ia64"。 |
| ProduceOnlyReferenceAssembly | .NET | 布林值，指示編譯器只發出參考組件，而不發出已編譯的程式碼。 無法與 `ProduceReferenceAssembly` 搭配使用。  此屬性對應於 *vbc.exe* 和 *csc.exe* 編譯器的 `/refonly` 參數。 |
| ProduceReferenceAssembly | .NET | 布林值，設定為 `true` 時會產生目前組件的[參考組件](/dotnet/standard/assembly/reference-assemblies)。 使用這項功能時，`Deterministic` 應該是 `true`。 此屬性對應於 *vbc.exe* 和 *csc.exe* 編譯器的 `/refout` 參數。 |
| RemoveIntegerChecks | Visual Basic | 布林值，指出是否要停用整數溢位錯誤檢查。 預設值是 `false`。 此屬性相當於 *vbc.exe* 編譯器的 `/removeintchecks` 參數。 |
| RootNamespace | 全部 | 命名內嵌資源時使用的根命名空間。 這個命名空間是內嵌資源資訊清單名稱的一部分。 |
| Satellite_AlgorithmId | .NET | 建立附屬組件時要使用之 *AL.exe* 雜湊演算法的 ID。 |
| Satellite_BaseAddress | .NET | 使用 `CreateSatelliteAssemblies` 目標建置文化特性特有的附屬組件時，要使用的基底位址。 |
| Satellite_CompanyName | .NET | 產生附屬組件期間要傳入 *AL.exe* 的公司名稱。 |
| Satellite_Configuration | .NET | 產生附屬組件期間要傳入 *AL.exe* 的組態名稱。 |
| Satellite_Description | .NET | 產生附屬組件期間要傳入 *AL.exe* 的描述文字。 |
| Satellite_EvidenceFile | .NET | 在資源名稱為 "Security.Evidence" 的附屬組件中內嵌指定的檔案。 |
| Satellite_FileVersion | .NET | 指定附屬組件中 [檔案版本] 欄位的字串。 |
| Satellite_Flags | .NET | 指定附屬組件中 [旗標] 欄位的值。 |
| Satellite_GenerateFullPaths | .NET | 設定讓建置工作針對錯誤訊息中報告的任何檔案使用絕對路徑。 |
| Satellite_LinkResource | .NET | 將指定的資源檔連結至附屬組件。 |
| Satellite_MainEntryPoint | .NET | 指定在產生附屬組件期間模組轉換成可執行檔時，用來做為進入點之方法的完整名稱 (也就是 class.method)。 |
| Satellite_ProductName | .NET | 指定附屬組件中 [產品] 欄位的字串。 |
| Satellite_ProductVersion | .NET | 指定附屬組件中 [ProductVersion] 欄位的字串。 |
| Satellite_TargetType | .NET | 將附屬組件輸出檔的檔案格式指定為 "library"、"exe" 或 "win"。 預設值為 "library"。 |
| Satellite_Title | .NET | 指定附屬組件中 [標題] 欄位的字串。 |
| Satellite_Trademark | .NET | 指定附屬組件中 [商標] 欄位的字串。 |
| Satellite_Version | .NET | 指定附屬組件的版本資訊。 |
| Satellite_Win32Icon | .NET | 將 *.ico* 圖示檔插入附屬組件。 |
| Satellite_Win32Resource | .NET | 將 Win32 資源 (*.res* 檔案) 插入附屬組件。 |
| SGenToolPath | .NET | 選擇性的工具路徑，指出目前版本的 *SGen.exe* 遭到覆寫時，取得 *SGen.exe* 的位置。 |
| SGenUseProxyTypes | .NET | 布林值，指出是否要由 *SGen.exe* 產生 Proxy 類型。 只有當 *GenerateSerializationAssemblies* 設定為 on 時，才適用這種情況。<br /><br /> SGen 目標會使用這個屬性設定 UseProxyTypes 旗標。 這個屬性預設為 true，而且沒有 UI 可用來變更這個屬性。 若要產生非 WebService 類型的序列化組件，請先將這個屬性新增至專案檔並將它設定為 false，再匯入 *Microsoft.Common.Targets* 或 *C#/VB.targets*。 |
| SkipInvalidConfigurations | 全部 | 若 `true` 為，則在不正確平臺和設定組合上產生警告，但不會使組建失敗; 當 `false` 或未定義 (預設) 時，會產生錯誤。 |
| StartupObject | .NET | 指定包含 Main 方法或 Sub Main 程序的類別或模組。 這個屬性相當於 `/main` 編譯器參數。 |
| SubsystemVersion | .NET | 指定所產生的可執行檔能夠使用的最低子系統版本。 這個屬性相當於 `/subsystemversion` 編譯器參數。 如需這個屬性之預設值的資訊，請參閱 [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) 或 [/subsystemversion (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option)。 |
| TargetCompactFramework | .NET | 執行您建置之應用程式所需的 .NET Compact Framework 版本。 指定這個屬性可讓您參考無法以其他方式參考的某些 Framework 組件。 |
| TargetFrameworkVersion | .NET | 執行您正在建置之應用程式所需的 .NET Framework 版本。 指定這個屬性可讓您參考無法以其他方式參考的某些 Framework 組件。 |
| TreatWarningsAsErrors | .NET | 布林值參數，如果為 `true`，表示會將所有警告視為錯誤。 這個參數 (Parameter) 相當於 `/nowarn` 編譯器參數 (Switch)。 |
| UseHostCompilerIfAvailable | .NET | 布林值參數，如果為 `true`，表示建置工作會使用同處理序 (In-Process) 編譯器物件 (如果有的話)。 此參數僅供 Visual Studio 使用。 |
| Utf8Output | .NET | 布林值參數，如果為 `true`，則會使用 UTF-8 編碼記錄編譯器輸出。 這個參數 (Parameter) 相當於 `/utf8Output` 編譯器參數 (Switch)。 |
| VbcToolPath | Visual Basic | 選擇性路徑，指出目前的 *vbc.exe* 版本遭到覆寫時，*vbc.exe* 的另一個位置。 |
| VbcVerbosity | Visual Basic | 指定 Visual Basic 編譯器輸出的詳細程度。 有效值為 "Quiet"、"Normal" (預設值) 或 "Verbose"。 |
| VisualStudioVersion | 全部 | 指定考慮用於執行這個專案的 Visual Studio 版本。 如果沒有指定這個屬性，MSBuild 會將它設定為合理的預設值。<br /><br /> 這個屬性會在數種專案類型中用來指定組建所使用的一組目標。 如果專案的 `ToolsVersion` 設定為 4.0 (含) 以上，則會使用 `VisualStudioVersion` 指定要使用的子工具組。 如需詳細資訊，請參閱 [Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)。 |
| WarningsAsErrors | .NET | 指定要視為錯誤的警告清單。 這個參數 (Parameter) 相當於 `/warnaserror` 編譯器參數 (Switch)。 |
| WarningsNotAsErrors | .NET | 指定不要視為錯誤的警告清單。 這個參數 (Parameter) 相當於 `/warnaserror` 編譯器參數 (Switch)。 |
| Win32Manifest | .NET | 應內嵌於最終組件中的資訊清單檔案名稱。 這個參數 (Parameter) 相當於 `/win32Manifest` 編譯器參數 (Switch)。 |
| Win32Resource | .NET | 要內嵌於最終組件中的 Win32 資源檔案名稱。 這個參數 (Parameter) 相當於 `/win32resource` 編譯器參數 (Switch)。 |

## <a name="see-also"></a>另請參閱

- [一般 MSBuild 專案項目](../msbuild/common-msbuild-project-items.md)
- [一般 MSBuild 項目中繼資料](common-msbuild-item-metadata.md)
- [MSBuild 保留和已知屬性](msbuild-reserved-and-well-known-properties.md)
- [.NET SDK 專案的 MSBuild 參考](/dotnet/core/project-sdk/msbuild-props)
