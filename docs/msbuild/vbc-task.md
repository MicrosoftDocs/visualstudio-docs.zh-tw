---
title: Vbc 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何使用 Vbc 工作包裝 vbc.exe，以產生可執行檔、動態連結程式庫或程式碼模組。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6596dd0893d0ab302a738cb12856fc6758df039
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908864"
---
# <a name="vbc-task"></a>Vbc 工作

包裝 *vbc.exe*，其會產生可執行檔 (*.Exe*) 、動態連結程式庫 (*.dll*) 或程式碼模組 (*. .netmodule*) 。 如需 *vbc.exe* 的詳細資訊，請參閱 [Visual Basic 命令列編譯器](/dotnet/visual-basic/reference/command-line-compiler/index)。

## <a name="parameters"></a>參數

 下表說明 `Vbc` 工作的參數。

| 參數 | Description |
|------------------------------| - |
| `AdditionalLibPaths` | 選擇性的 `String[]` 參數。<br /><br /> 指定其他資料夾，在其中尋找參考屬性中指定的組件。 |
| `AddModules` | 選擇性的 `String[]` 參數。<br /><br /> 讓編譯器將所指定檔案的類型資訊全部提供給您目前編譯的專案。 這個參數對應于 *vbc.exe* 編譯器的 [-addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule)參數。 |
| `BaseAddress` | 選擇性的 `String` 參數。<br /><br /> 指定 DLL 的基底位址。 這個參數對應于 *vbc.exe* 編譯器的 [-baseaddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress)參數。 |
| `CodePage` | 選擇性的 `Int32` 參數。<br /><br /> 指定編譯過程中所有原始程式碼檔使用的字碼頁。 這個參數對應于 *vbc.exe* 編譯器的 [-字碼頁](/dotnet/visual-basic/reference/command-line-compiler/codepage)參數。 |
| `DebugType` | 選擇性的 `String[]` 參數。<br /><br /> 造成編譯器產生偵錯資訊。 此參數的值如下：<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> 預設值為 `full`，可將偵錯工具附加至執行中的程式。 `pdbonly` 值可於偵錯工具中啟動程式時，讓原始程式碼進行偵錯，但只有當執行中的程式附加在偵錯工具時，才會顯示組合語言程式碼。 如需詳細資訊，請參閱 [-debug (Visual Basic) ](/dotnet/visual-basic/reference/command-line-compiler/debug)。 |
| `DefineConstants` | 選擇性的 `String[]` 參數。<br /><br /> 定義條件式編譯器常數。 符號/值組會以分號分隔，並且使用下列語法指定：<br /><br /> *symbol1* `=` *value1* `;` *symbol2* `=` *value2*<br /><br /> 這個參數對應于 *vbc.exe* 編譯器的 [-define](/dotnet/visual-basic/reference/command-line-compiler/define)參數。 |
| `DelaySign` | 選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，工作會將公開金鑰放在組件中。 如為 `false`，工作會完整簽署組件。 預設值為 `false`。此參數除非搭配 `KeyFile` 參數或 `KeyContainer` 參數使用，否則沒有任何作用。 這個參數對應于 *vbc.exe* 編譯器的 [-delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign)參數。 |
| `Deterministic` | 選擇性的 `Boolean` 參數。<br/><br/> 若為 `true`，可讓編譯器輸出在輸入相同時編譯之間二進位內容相同的組件。<br/><br/>如需詳細資訊，請參閱 [-deterministic](/dotnet/visual-basic/reference/command-line-compiler/deterministic)。 |
| `DisabledWarnings` | 選擇性的 `String` 參數。<br /><br /> 隱藏指定的警告。 您只需要指定警告識別項的數值部分。 若有多個警告，則會以分號分隔。 這個參數對應于 *vbc.exe* 編譯器的 [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)參數。 |
| `DocumentationFile` | 選擇性的 `String` 參數。<br /><br /> 將文件註解處理成指定的 XML 檔案。 此參數會覆寫 `GenerateDocumentation` 屬性。 如需詳細資訊，請參閱 [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc)。 |
| `EmitDebugInformation` | 選擇性的 `Boolean` 參數。<br /><br /> 如果 `true` 為，則工作會產生調試資訊，並將其放在 *.pdb* 檔案中。 如需詳細資訊，請參閱 [-debug (Visual Basic) ](/dotnet/visual-basic/reference/command-line-compiler/debug)。 |
| `ErrorReport` | 選擇性的 `String` 參數。<br /><br /> 指定工作應如何報告編譯器內部錯誤。 此參數的值如下：<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> 如果指定 `prompt` 且發生編譯器內部錯誤時，會提示使用者選擇是否將錯誤資料傳送給 Microsoft。<br /><br /> 如果指定 `send` 且發生編譯器內部錯誤時，工作會將錯誤資料傳送給 Microsoft。<br /><br /> 預設值為 `none`，僅報告文字輸出中的錯誤。<br /><br /> 這個參數對應于 *vbc.exe* 編譯器的 [-errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport)參數。 |
| `FileAlignment` | 選擇性的 `Int32` 參數。<br /><br /> 以位元組為單位，指定要對齊輸出檔案區段的位置。 此參數的值如下：<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> 這個參數對應于 *vbc.exe* 編譯器的 [-filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign)參數。 |
| `GenerateDocumentation` | 選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true` 則產生文件資訊，並將該資訊放入 XML 檔中，此檔案的名稱為工作所建立的可執行檔或程式庫名稱。 如需詳細資訊，請參閱 [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc)。 |
| `Imports` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 從指定的項目集合匯入命名空間。 此參數對應于 *vbc.exe* 編譯器的 [-imports](/dotnet/visual-basic/reference/command-line-compiler/imports)參數。 |
| `KeyContainer` | 選擇性的 `String` 參數。<br /><br /> 指定密碼編譯金鑰容器的名稱。 此參數對應至 *vbc.exe* 編譯器的 [-keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) 參數。 |
| `KeyFile` | 選擇性的 `String` 參數。<br /><br /> 指定包含密碼編譯金鑰的檔名。 如需詳細資訊，請參閱 [-keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile)。 |
| `LangVersion` | 選擇性的 <xref:System.String?displayProperty=fullName> 參數。<br /><br /> 指定[語言版本](/dotnet/visual-basic/language-reference/configure-language-version)，例如 "15.5"。 |
| `LinkResources` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 在輸出檔中建立 .NET Framework 資源的連結；不要將資源檔放置於輸出檔中。 這個參數對應于 *vbc.exe* 編譯器的 [-linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource)參數。 |
| `MainEntryPoint` | 選擇性的 `String` 參數。<br /><br /> 指定包含 `Sub Main` 程序的類別或模組。 這個參數對應於 *vbc.exe* 編譯器的 [-main](/dotnet/visual-basic/reference/command-line-compiler/main) 參數。 |
| `ModuleAssemblyName` | 選擇性的 `String` 參數。<br /><br /> 指定將包含此模組的組件。 |
| `NoConfig` | 選擇性的 `Boolean` 參數。<br /><br /> 指定編譯器不應使用 *vbc* 檔。 這個參數對應于 *vbc.exe* 編譯器的 [-noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig)參數。 |
| `NoLogo` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即會隱藏顯示編譯器橫幅資訊。 這個參數對應于 *vbc.exe* 編譯器的 [-nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo)參數。 |
| `NoStandardLib` | 選擇性的 `Boolean` 參數。<br /><br /> 使編譯器不要參考標準程式庫。 這個參數對應于 *vbc.exe* 編譯器的 [-nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib)參數。 |
| `NoVBRuntimeReference` | 選擇性的 `Boolean` 參數。<br /><br /> 僅供內部使用。 若為 true，則會防止自動參考 *Microsoft.VisualBasic.dll*。 |
| `NoWarnings` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，工作便會隱藏所有警告。 如需詳細資訊，請參閱 [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)。 |
| `Optimize` | 選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，則啟用編譯器最佳化。 此參數對應于 *vbc.exe* 編譯器的 [-optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize)參數。 |
| `OptionCompare` | 選擇性的 `String` 參數。<br /><br /> 指定如何進行字串比較。 此參數的值如下：<br /><br /> -   `binary`<br />-   `text`<br /><br /> 值 `binary` 指定此工作使用二進位字串比較。 值 `text` 指定此工作使用文字字串比較。 此參數的預設值為 `binary`。 這個參數對應于 *vbc.exe* 編譯器的 [-optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare)參數。 |
| `OptionExplicit` | 選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，則需要明確宣告變數。 這個參數對應于 *vbc.exe* 編譯器的 [-optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit)參數。 |
| `OptionInfer` | 選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，允許變數的類型推斷。 |
| `OptionStrict` | 選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，工作會強制執行嚴格的類型語意來限制隱含類型轉換。 這個參數對應于 *vbc.exe* 編譯器的 [-optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)參數。 |
| `OptionStrictType` | 選擇性的 `String` 參數。<br /><br /> 指定哪些嚴格的類型語意會產生警告。 目前只支援 "custom"。 這個參數對應于 *vbc.exe* 編譯器的 [-optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)參數。 |
| `OutputAssembly` | 選擇性的 `String` 輸出參數。<br /><br /> 指定輸出檔案的名稱。 這個參數對應于 *vbc.exe* 編譯器的 [out](/dotnet/visual-basic/reference/command-line-compiler/out)參數。 |
| `Platform` | 選擇性的 `String` 參數。<br /><br /> 指定輸出檔設為目標的處理器平台。 這個參數可以具有 `x86`、`x64`、`Itanium` 或 `anycpu` 的值。 預設為 `anycpu`。 此參數對應于 *vbc.exe* 編譯器的 [-platform](/dotnet/visual-basic/reference/command-line-compiler/platform)參數。 |
| `References` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 導致工作將公用類型資訊從指定的項目匯入目前的專案。 這個參數對應于 *vbc.exe* 編譯器的 [-reference](/dotnet/visual-basic/reference/command-line-compiler/reference)參數。 |
| `RemoveIntegerChecks` | 選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，停用整數的溢位錯誤檢查。 預設值是 `false`。 這個參數對應于 *vbc.exe* 編譯器的 [-removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks)參數。 |
| `Resources` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 將 .NET Framework 資源內嵌到輸出檔中。 此參數對應于 *vbc.exe* 編譯器的 [-resource](/dotnet/visual-basic/reference/command-line-compiler/resource)參數。 |
| `ResponseFiles` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定包含適用於此工作之命令的回應檔。 此參數會對應至 *vbc.exe* 編譯器的 [@ (指定回應檔)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file)選項。 |
| `RootNamespace` | 選擇性的 `String` 參數。<br /><br /> 指定所有類型宣告的根命名空間。 這個參數對應于 *vbc.exe* 編譯器的 [-rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace)參數。 |
| `SdkPath` | 選擇性的 `String` 參數。<br /><br /> 指定 *mscorlib.dll* 和 *microsoft.visualbasic.dll* 的位置。 這個參數對應于 *vbc.exe* 編譯器的 [-sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath)參數。 |
| `Sources` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定一或多個 Visual Basic 來源檔案。 |
| `TargetCompactFramework` | 選擇性的 `Boolean` 參數。<br /><br /> 如果 `true` 為，則工作會以 .NET Compact Framework 為目標。 此參數對應于 *vbc.exe* 編譯器的 [-netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf)參數。 |
| `TargetType` | 選擇性的 `String` 參數。<br /><br /> 指定輸出檔的檔案格式。 此參數的值如下：`library` (可建立程式碼程式庫)、`exe` (可建立主控台應用程式)、`module` (可建立模組) 或 `winexe` (可建立 Windows 程式)。 預設為 `library`。 這個參數對應于 *vbc.exe* 編譯器的 [-target](/dotnet/visual-basic/reference/command-line-compiler/target)參數。 |
| `Timeout` | 選擇性的 `Int32` 參數。<br /><br /> 指定時間量 (以毫秒為單位)，在此時間量之後會終止工作可執行檔。 預設值是 `Int.MaxValue`，表示沒有逾時期間。 |
| `ToolPath` | 選擇性的 `String` 參數。<br /><br /> 指定工作將載入基礎可執行檔的位置， (*vbc.exe*) 。 如果未指定此參數，工作會使用 SDK 安裝路徑，對應至執行 MSBuild 的 framework 版本。 |
| `TreatWarningsAsErrors` | 選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，所有警告都視為錯誤。 如需詳細資訊，請參閱 [-warnaserror (Visual Basic) ](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)。 |
| `UseHostCompilerIfAvailable` | 選擇性的 `Boolean` 參數。<br /><br /> 如果有的話，即會指示工作來使用同處理序編譯器物件。 僅 Visual Studio 使用。 |
| `Utf8Output` | 選擇性的 `Boolean` 參數。<br /><br /> 使用 UTF-8 編碼記錄編譯器輸出。 這個參數對應于 *vbc.exe* 編譯器的 [-utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output)參數。 |
| `Verbosity` | 選擇性的 `String` 參數。<br /><br /> 指定編譯器輸出的詳細資訊。 詳細資訊可以是 `Quiet`、`Normal` (預設值) 或 `Verbose`。 |
| `WarningsAsErrors` | 選擇性的 `String` 參數。<br /><br /> 指定要視為錯誤的警告清單。 如需詳細資訊，請參閱 [-warnaserror (Visual Basic) ](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)。<br /><br /> 此參數會覆寫 `TreatWarningsAsErrors` 參數。 |
| `WarningsNotAsErrors` | 選擇性的 `String` 參數。<br /><br /> 指定不要視為錯誤的警告清單。 如需詳細資訊，請參閱 [-warnaserror (Visual Basic) ](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)。<br /><br /> 唯有將 `TreatWarningsAsErrors` 參數設為 `true` 時，此參數才有用。 |
| `Win32Icon` | 選擇性的 `String` 參數。<br /><br /> 在組件中插入 *.ico* 檔案，讓輸出檔在 [檔案總管] 中具有所需的外觀。 這個參數對應于 *vbc.exe* 編譯器的 [-win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon)參數。 |
| `Win32Resources` | 選擇性的 `String` 參數。<br /><br /> 將 Win32 資源 (*.res*) 檔案插入輸出檔中。 這個參數對應于 *vbc.exe* 編譯器的 [-win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource)參數。 |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

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

- [Visual Basic 命令列編譯器](/dotnet/visual-basic/reference/command-line-compiler/index)
- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
