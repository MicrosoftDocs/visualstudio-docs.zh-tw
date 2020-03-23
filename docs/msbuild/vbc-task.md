---
title: Vbc 工作 | Microsoft Docs
ms.date: 04/12/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Vbc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Vbc task [MSBuild]
- MSBuild, Vbc task
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a1710336ebc73be707e962733e37376b5689e10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631233"
---
# <a name="vbc-task"></a>Vbc 工作

包裝*vbc.exe*，它生成可執行檔 *（.exe）、* 動態連結程式庫 *（.dll）* 或代碼*模組 （.netmodule）。* 有關*vbc.exe*的詳細資訊，請參閱[可視基本命令列編譯器](/dotnet/visual-basic/reference/command-line-compiler/index)。

## <a name="parameters"></a>參數

 下表說明 `Vbc` 工作的參數。

| 參數 | 描述 |
|------------------------------| - |
| `AdditionalLibPaths` | 選擇性的 `String[]` 參數。<br /><br /> 指定其他資料夾，在其中尋找參考屬性中指定的組件。 |
| `AddModules` | 選擇性的 `String[]` 參數。<br /><br /> 讓編譯器將所指定檔案的類型資訊全部提供給您目前編譯的專案。 此參數對應于*vbc.exe*編譯器的[-addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule)開關。 |
| `BaseAddress` | 選擇性的 `String` 參數。<br /><br /> 指定 DLL 的基底位址。 此參數對應于*vbc.exe*編譯器的[-基底位址](/dotnet/visual-basic/reference/command-line-compiler/baseaddress)開關。 |
| `CodePage` | 選擇性的 `Int32` 參數。<br /><br /> 指定編譯過程中所有原始程式碼檔使用的字碼頁。 此參數對應于*vbc.exe*編譯器的[-字碼頁](/dotnet/visual-basic/reference/command-line-compiler/codepage)開關。 |
| `DebugType` | 選擇性的 `String[]` 參數。<br /><br /> 造成編譯器產生偵錯資訊。 此參數的值如下：<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> 預設值為 `full`，可將偵錯工具附加至執行中的程式。 `pdbonly` 值可於偵錯工具中啟動程式時，讓原始程式碼進行偵錯，但只有當執行中的程式附加在偵錯工具時，才會顯示組合語言程式碼。 有關詳細資訊，請參閱[-調試（可視基本）](/dotnet/visual-basic/reference/command-line-compiler/debug)。 |
| `DefineConstants` | 選擇性的 `String[]` 參數。<br /><br /> 定義條件式編譯器常數。 符號/值組會以分號分隔，並且使用下列語法指定：<br /><br /> *symbol1* `=` *value1* `;` *symbol2* `=` *value2*<br /><br /> 此參數對應于*vbc.exe*編譯器的[-define](/dotnet/visual-basic/reference/command-line-compiler/define)開關。 |
| `DelaySign` | 選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，工作會將公開金鑰放在組件中。 如為 `false`，工作會完整簽署組件。 預設值為 `false`。此參數除非搭配 `KeyFile` 參數或 `KeyContainer` 參數使用，否則沒有任何作用。 此參數對應于*vbc.exe*編譯器的[-delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign)開關。 |
| `Deterministic` | 選擇性的 `Boolean` 參數。<br/><br/> 若為 `true`，可讓編譯器輸出在輸入相同時編譯之間二進位內容相同的組件。<br/><br/>如需詳細資訊，請參閱 [-deterministic](/dotnet/visual-basic/reference/command-line-compiler/deterministic)。 |
| `DisabledWarnings` | 選擇性的 `String` 參數。<br /><br /> 隱藏指定的警告。 您只需要指定警告識別項的數值部分。 若有多個警告，則會以分號分隔。 此參數對應于*vbc.exe*編譯器的[-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)開關。 |
| `DocumentationFile` | 選擇性的 `String` 參數。<br /><br /> 將文件註解處理成指定的 XML 檔案。 此參數會覆寫 `GenerateDocumentation` 屬性。 有關詳細資訊，請參閱[-doc](/dotnet/visual-basic/reference/command-line-compiler/doc)。 |
| `EmitDebugInformation` | 選擇性的 `Boolean` 參數。<br /><br /> 如果`true`，任務將生成調試資訊並將其放在 *.pdb*檔中。 有關詳細資訊，請參閱[-調試（可視基本）](/dotnet/visual-basic/reference/command-line-compiler/debug)。 |
| `ErrorReport` | 選擇性的 `String` 參數。<br /><br /> 指定工作應如何報告編譯器內部錯誤。 此參數的值如下：<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> 如果指定 `prompt` 且發生編譯器內部錯誤時，會提示使用者選擇是否將錯誤資料傳送給 Microsoft。<br /><br /> 如果指定 `send` 且發生編譯器內部錯誤時，工作會將錯誤資料傳送給 Microsoft。<br /><br /> 預設值為 `none`，僅報告文字輸出中的錯誤。<br /><br /> 此參數對應于*vbc.exe*編譯器的[-錯誤報表](/dotnet/visual-basic/reference/command-line-compiler/errorreport)開關。 |
| `FileAlignment` | 選擇性的 `Int32` 參數。<br /><br /> 以位元組為單位，指定要對齊輸出檔案區段的位置。 此參數的值如下：<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> 此參數對應于*vbc.exe*編譯器的[-filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign)開關。 |
| `GenerateDocumentation` | 選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true` 則產生文件資訊，並將該資訊放入 XML 檔中，此檔案的名稱為工作所建立的可執行檔或程式庫名稱。 有關詳細資訊，請參閱[-doc](/dotnet/visual-basic/reference/command-line-compiler/doc)。 |
| `Imports` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 從指定的項目集合匯入命名空間。 此參數對應于*vbc.exe*編譯器的[-導入](/dotnet/visual-basic/reference/command-line-compiler/imports)開關。 |
| `KeyContainer` | 選擇性的 `String` 參數。<br /><br /> 指定密碼編譯金鑰容器的名稱。 此參數對應至 *vbc.exe* 編譯器的 [-keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) 參數。 |
| `KeyFile` | 選擇性的 `String` 參數。<br /><br /> 指定包含密碼編譯金鑰的檔名。 有關詳細資訊，請參閱[-keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile)。 |
| `LangVersion` | 選擇性的 <xref:System.String?displayProperty=fullName> 參數。<br /><br /> 指定[語言版本](/dotnet/visual-basic/language-reference/configure-language-version)，例如 "15.5"。 |
| `LinkResources` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 在輸出檔中建立 .NET Framework 資源的連結；不要將資源檔放置於輸出檔中。 此參數對應于*vbc.exe*編譯器的[-link 資源](/dotnet/visual-basic/reference/command-line-compiler/linkresource)開關。 |
| `MainEntryPoint` | 選擇性的 `String` 參數。<br /><br /> 指定包含 `Sub Main` 程序的類別或模組。 這個參數對應於 *vbc.exe* 編譯器的 [-main](/dotnet/visual-basic/reference/command-line-compiler/main) 參數。 |
| `ModuleAssemblyName` | 選擇性的 `String` 參數。<br /><br /> 指定將包含此模組的組件。 |
| `NoConfig` | 選擇性的 `Boolean` 參數。<br /><br /> 指定編譯器不應使用*vbc.rsp*檔。 此參數對應于*vbc.exe*編譯器的[-noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig)參數。 |
| `NoLogo` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即會隱藏顯示編譯器橫幅資訊。 此參數對應于*vbc.exe*編譯器的[-nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo)開關。 |
| `NoStandardLib` | 選擇性的 `Boolean` 參數。<br /><br /> 使編譯器不要參考標準程式庫。 此參數對應于*vbc.exe*編譯器的[-nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib)開關。 |
| `NoVBRuntimeReference` | 選擇性的 `Boolean` 參數。<br /><br /> 僅供內部使用。 如果為 true，則阻止自動引用*Microsoft。* |
| `NoWarnings` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，工作便會隱藏所有警告。 有關詳細資訊，請參閱[-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)。 |
| `Optimize` | 選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，則啟用編譯器最佳化。 此參數對應于*vbc.exe*編譯器的[-優化](/dotnet/visual-basic/reference/command-line-compiler/optimize)開關。 |
| `OptionCompare` | 選擇性的 `String` 參數。<br /><br /> 指定如何進行字串比較。 此參數的值如下：<br /><br /> -   `binary`<br />-   `text`<br /><br /> 值 `binary` 指定此工作使用二進位字串比較。 值 `text` 指定此工作使用文字字串比較。 此參數的預設值為 `binary`。 此參數對應于*vbc.exe*編譯器的[-option 比較](/dotnet/visual-basic/reference/command-line-compiler/optioncompare)開關。 |
| `OptionExplicit` | 選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，則需要明確宣告變數。 此參數對應于*vbc.exe*編譯器的[-option 顯式](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit)開關。 |
| `OptionInfer` | 選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，允許變數的類型推斷。 |
| `OptionStrict` | 選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，工作會強制執行嚴格的類型語意來限制隱含類型轉換。 此參數對應于*vbc.exe*編譯器的[-option 嚴格](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)開關。 |
| `OptionStrictType` | 選擇性的 `String` 參數。<br /><br /> 指定哪些嚴格的類型語意會產生警告。 目前只支援 "custom"。 此參數對應于*vbc.exe*編譯器的[-option 嚴格](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)開關。 |
| `OutputAssembly` | 選擇性的 `String` 輸出參數。<br /><br /> 指定輸出檔案的名稱。 此參數對應于*vbc.exe*編譯器的[-out](/dotnet/visual-basic/reference/command-line-compiler/out)開關。 |
| `Platform` | 選擇性的 `String` 參數。<br /><br /> 指定輸出檔設為目標的處理器平台。 這個參數可以具有 `x86`、`x64`、`Itanium` 或 `anycpu` 的值。 預設值為 `anycpu`。 此參數對應于*vbc.exe*編譯器的[-平臺](/dotnet/visual-basic/reference/command-line-compiler/platform)交換器。 |
| `References` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 導致工作將公用類型資訊從指定的項目匯入目前的專案。 此參數對應于*vbc.exe*編譯器的[-引用](/dotnet/visual-basic/reference/command-line-compiler/reference)開關。 |
| `RemoveIntegerChecks` | 選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，停用整數的溢位錯誤檢查。 預設值是 `false`。 此參數對應于*vbc.exe*編譯器的[-removeint檢查](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks)開關。 |
| `Resources` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 將 .NET Framework 資源內嵌到輸出檔中。 此參數對應于*vbc.exe*編譯器的[-資源](/dotnet/visual-basic/reference/command-line-compiler/resource)開關。 |
| `ResponseFiles` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定包含適用於此工作之命令的回應檔。 此參數對應于*vbc.exe*編譯器的[#（指定回應檔）](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file)選項。 |
| `RootNamespace` | 選擇性的 `String` 參數。<br /><br /> 指定所有類型宣告的根命名空間。 此參數對應于*vbc.exe*編譯器的[-rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace)開關。 |
| `SdkPath` | 選擇性的 `String` 參數。<br /><br /> 指定*mscorlib.dll*和*Microsoft.visualbasic.dll*的位置。 此參數對應于*vbc.exe*編譯器的[-sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath)開關。 |
| `Sources` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定一或多個 Visual Basic 來源檔案。 |
| `TargetCompactFramework` | 選擇性的 `Boolean` 參數。<br /><br /> 如果`true`，任務將目標為 .NET 緊湊框架。 此開關對應于*vbc.exe*編譯器的[-netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf)開關。 |
| `TargetType` | 選擇性的 `String` 參數。<br /><br /> 指定輸出檔的檔案格式。 此參數的值如下：`library` (可建立程式碼程式庫)、`exe` (可建立主控台應用程式)、`module` (可建立模組) 或 `winexe` (可建立 Windows 程式)。 預設值為 `library`。 此參數對應于*vbc.exe*編譯器的[-目標](/dotnet/visual-basic/reference/command-line-compiler/target)開關。 |
| `Timeout` | 選擇性的 `Int32` 參數。<br /><br /> 指定時間量 (以毫秒為單位)，在此時間量之後會終止工作可執行檔。 預設值是 `Int.MaxValue`，表示沒有逾時期間。 |
| `ToolPath` | 選擇性的 `String` 參數。<br /><br /> 指定任務從何處載入基礎可執行檔 *（vbc.exe）* 的位置。 如果未指定此參數，則任務將使用與運行 MSBuild 的框架版本對應的 SDK 安裝路徑。 |
| `TreatWarningsAsErrors` | 選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，所有警告都視為錯誤。 有關詳細資訊，請參閱[-警告錯誤（視覺基本）](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)。 |
| `UseHostCompilerIfAvailable` | 選擇性的 `Boolean` 參數。<br /><br /> 如果有的話，即會指示工作來使用同處理序編譯器物件。 僅 Visual Studio 使用。 |
| `Utf8Output` | 選擇性的 `Boolean` 參數。<br /><br /> 使用 UTF-8 編碼記錄編譯器輸出。 此參數對應于*vbc.exe*編譯器的[-utf8 輸出](/dotnet/visual-basic/reference/command-line-compiler/utf8output)開關。 |
| `Verbosity` | 選擇性的 `String` 參數。<br /><br /> 指定編譯器輸出的詳細資訊。 詳細資訊可以是 `Quiet`、`Normal` (預設值) 或 `Verbose`。 |
| `WarningsAsErrors` | 選擇性的 `String` 參數。<br /><br /> 指定要視為錯誤的警告清單。 有關詳細資訊，請參閱[-警告錯誤（視覺基本）](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)。<br /><br /> 此參數會覆寫 `TreatWarningsAsErrors` 參數。 |
| `WarningsNotAsErrors` | 選擇性的 `String` 參數。<br /><br /> 指定不要視為錯誤的警告清單。 有關詳細資訊，請參閱[-警告錯誤（視覺基本）](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)。<br /><br /> 唯有將 `TreatWarningsAsErrors` 參數設為 `true` 時，此參數才有用。 |
| `Win32Icon` | 選擇性的 `String` 參數。<br /><br /> 在組件中插入 *.ico* 檔案，讓輸出檔在 [檔案總管]**** 中具有所需的外觀。 此參數對應于*vbc.exe*編譯器的[-win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon)開關。 |
| `Win32Resources` | 選擇性的 `String` 參數。<br /><br /> 在輸出檔案中插入 Win32 資源 （*.res*） 檔。 此參數對應于*vbc.exe*編譯器的[-win32 資源](/dotnet/visual-basic/reference/command-line-compiler/win32resource)開關。 |

## <a name="remarks"></a>備註

 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.ToolTask> 類別。 有關這些附加參數及其說明的清單，請參閱[ToolTask 擴展基類](../msbuild/tooltaskextension-base-class.md)。

## <a name="example"></a>範例

 下列範例會編譯 Visual Basic 專案。

```xml
<VBC
   Sources="@(sources)"
   Resources="strings.resources"
   Optimize="true"
   OutputAssembly="out.exe"/>
```

## <a name="see-also"></a>另請參閱

- [可視基本命令列編譯器](/dotnet/visual-basic/reference/command-line-compiler/index)
- [工作](../msbuild/msbuild-tasks.md)
- [任務引用](../msbuild/msbuild-task-reference.md)
