---
title: Csc 工作 | Microsoft Docs
description: '本文描述 MSBuild Csc 工作，此工作會包裝 c # 編譯器、csc.exe，並產生 .exe、.dll 或 .netmodule 檔案。'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Csc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Csc task [MSBuild]
- MSBuild, Csc task
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a3787d5aa21e029ab4900bdd89c88f1cc60f3489
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901349"
---
# <a name="csc-task"></a>Csc 工作

包裝 csc.exe，並產生可執行檔 (.*exe* 檔案)、動態連結程式庫 (*.dll* 檔案) 或程式碼模組 (.netmodule 檔案)。 如需 *csc.exe* 的詳細資訊，請參閱 [C# 編譯器選項](/dotnet/csharp/language-reference/compiler-options/index)。

## <a name="parameters"></a>參數

下表說明 `Csc` 工作的參數。

| 參數 | Description |
|------------------------------| - |
| `AdditionalLibPaths` | 選擇性的 `String[]` 參數。<br /><br /> 指定要搜尋參考的其他目錄。 如需詳細資訊，請參閱 [-lib (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option)。 |
| `AddModules` | 選擇性的 `String` 參數。<br /><br /> 指定要成為組件一部分的一個或多個模組。 如需詳細資訊，請參閱 [-addmodule (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option)。 |
| `AllowUnsafeBlocks` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即會編譯使用 [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) 關鍵字的程式碼。 如需詳細資訊，請參閱 [-unsafe (c # 編譯器選項) ](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option)。 |
| `ApplicationConfiguration` | 選擇性的 `String` 參數。<br /><br /> 指定包含組件繫結設定的應用程式組態檔。 |
| `BaseAddress` | 選擇性的 `String` 參數。<br /><br /> 指定載入 DLL 時慣用的基底位址。 DLL 的預設基底位址是由 .NET Framework Common Language Runtime 所設定。 如需詳細資訊，請參閱 [-baseaddress (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option)。 |
| `CheckForOverflowUnderflow` | 選擇性的 `Boolean` 參數。<br /><br /> 指定超出資料類型範圍的整數算術，是否會導致在執行階段發生例外狀況。 如需詳細資訊，請參閱 [-checked (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option)。 |
| `CodePage` | 選擇性的 `Int32` 參數。<br /><br /> 指定編譯過程中所有原始程式碼檔使用的字碼頁。 如需詳細資訊，請參閱 [-codepage (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option)。 |
| `DebugType` | 選擇性的 `String` 參數。<br /><br /> 指定偵錯類型。 `DebugType` 可以是 `full` 或 `pdbonly`。 預設值是 `full`，會將偵錯工具附加至執行中的程式。 指定 `pdbonly`，讓原始程式碼在偵錯工具中啟動程式時進行偵錯，但只有在將執行中的程式附加到偵錯工具時，才會顯示組譯工具。<br /><br /> 此參數會覆寫 `EmitDebugInformation` 參數。<br /><br /> 如需詳細資訊，請參閱 [-debug (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option)。 |
| `DefineConstants` | 選擇性的 `String` 參數。<br /><br /> 定義前置處理器符號。 如需詳細資訊，請參閱 [-define (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option)。 |
| `DelaySign` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，則表示您只想將公開金鑰放置於組件中。 如果 `false` 為，則表示您想要完整簽署的元件<br /><br /> 除非與 `KeyFile` 或 `KeyContainer` 參數搭配使用，否則此參數沒有任何作用。<br /><br /> 如需詳細資訊，請參閱 [-delaysign (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option)。 |
| `Deterministic` | 選擇性的 `Boolean` 參數。<br/><br/> 若為 `true`，可讓編譯器輸出在輸入相同時編譯之間二進位內容相同的組件。<br/><br/>如需詳細資訊，請參閱 [-deterministic (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/deterministic-compiler-option)。 |
| `DisabledWarnings` | 選擇性的 `String` 參數。<br /><br /> 指定要停用的警告清單。 如需詳細資訊，請參閱 [-nowarn (c # 編譯器選項) ](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option)。 |
| `DocumentationFile` | 選擇性的 `String` 參數。<br /><br /> 將文件註解處理成 XML 檔案。 如需詳細資訊，請參閱 [-doc (c # 編譯器選項) ](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option)。 |
| `EmitDebugInformation` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，工作就會產生偵錯資訊，並將其放在程式資料庫 (.pdb) 檔案中。 如果是 `false`，工作就不會發出任何偵錯資訊。 預設為 `false`。 如需詳細資訊，請參閱 [-debug (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option)。 |
| `ErrorReport` | 選擇性的 `String` 參數。<br /><br /> 提供將 C# 內部錯誤回報給 Microsoft 的便利方式。 此參數可以具有 `prompt`、`send` 或 `none` 的值。 如果將此參數設為 `prompt`，您將會在編譯器內部錯誤發生時收到提示。 此提示可讓您以電子方式將錯誤報告傳送給 Microsoft。 如果將此參數設為 `send`，就會自動傳送錯誤報告。 如果將此參數設為 `none`，則只會在編譯器的文字輸出中報告錯誤。 預設為 `none`。 如需詳細資訊，請參閱 [-errorreport (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option)。 |
| `FileAlignment` | 選擇性的 `Int32` 參數。<br /><br /> 指定輸出檔案中區段的大小。 如需詳細資訊，請參閱 [-filealign (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option)。 |
| `GenerateFullPaths` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即會在編譯器輸出中指定檔案的絕對路徑。 如果是 `false`，則會指定檔案的名稱。 預設為 `false`。 如需詳細資訊，請參閱 [-fullpaths (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option)。 |
| `KeyContainer` | 選擇性的 `String` 參數。<br /><br /> 指定密碼編譯金鑰容器的名稱。 如需詳細資訊，請參閱 [-keycontainer (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option)。 |
| `KeyFile` | 選擇性的 `String` 參數。<br /><br /> 指定包含密碼編譯金鑰的檔名。 如需詳細資訊，請參閱 [-keyfile (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option)。 |
| `LangVersion` | 選擇性的 `String` 參數。<br /><br /> 指定要使用的語言版本。 如需詳細資訊，請參閱 [-langversion (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option)。 |
| `LinkResources` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 在輸出檔中建立 .NET Framework 資源的連結；不要將資源檔放置於輸出檔中。<br /><br /> 傳遞到此參數的項目可以具備名為 `LogicalName` 和 `Access` 的選擇性中繼資料項目。 `LogicalName` 會對應至 `/linkresource` 參數 (Switch) 的 `identifier` 參數 (Parameter)，而 `Access` 會對應至 `accessibility-modifier` 參數 (Parameter)。 如需詳細資訊，請參閱 [-linkresource (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option)。 |
| `MainEntryPoint` | 選擇性的 `String` 參數。<br /><br /> 指定 `Main` 方法的位置。 如需詳細資訊，請參閱 [-main (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option)。 |
| `ModuleAssemblyName` | 選擇性的 `String` 參數。<br /><br /> 指定將包含此模組的組件名稱。 |
| `NoConfig` | 選擇性的 `Boolean` 參數。<br /><br /> 若為 `true`，即會指示編譯器不要使用 *csc.rsp* 檔案進行編譯。 如需詳細資訊，請參閱 [-noconfig (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option)。 |
| `NoLogo` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即會隱藏顯示編譯器橫幅資訊。 如需詳細資訊，請參閱 [-nologo (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option)。 |
| `NoStandardLib` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即會防止匯入 *mscorlib.dll*，此檔案會定義整個系統命名空間。 如果您想要定義或建立自己的系統命名空間和物件，請使用此參數。 如需詳細資訊，請參閱 [-nostdlib (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option)。 |
| `NoWin32Manifest` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，就不會包含預設的 Win32 資訊清單。 |
| `Optimize` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即會啟用最佳化。 如果是 `false`，則會停用最佳化。 如需詳細資訊，請參閱 [-optimize (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option)。 |
| `OutputAssembly` | 選擇性的 `String` 輸出參數。<br /><br /> 指定輸出檔案的名稱。 如需詳細資訊，請參閱 [-out (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option)。 |
| `OutputRefAssembly` | 選擇性的 `String` 參數。<br /><br /> 指定輸出參考組件檔的名稱。 如需詳細資訊，請參閱 [-refout (c # 編譯器選項) ](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option)。 |
| `PdbFile` | 選擇性的 `String` 參數。<br /><br /> 指定偵錯資訊檔案名稱。 預設名稱是副檔名為 *.pdb* 的輸出檔案名稱。 |
| `Platform` | 選擇性的 `String` 參數。<br /><br /> 指定輸出檔設為目標的處理器平台。 此參數可以具有 `x86`、`x64` 或 `anycpu` 的值。 預設為 `anycpu`。 如需詳細資訊，請參閱 [-platform (c # 編譯器選項) ](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)。 |
| `References` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 導致工作將公用類型資訊從指定的項目匯入目前的專案。 如需詳細資訊，請參閱 [-reference (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option)。<br /><br /> 您可以藉由將中繼資料加入至原始的「參考」專案，在 MSBuild 檔案中指定 c # 參考別名 `Aliases` 。 例如，若要在下列 Csc 命令列中設定別名 "LS1"：<br /><br /> `CSC /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> 您可以使用：<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>` |
| `Resources` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 將 .NET Framework 資源內嵌到輸出檔中。<br /><br /> 傳遞到此參數的項目可以具備名為 `LogicalName` 和 `Access` 的選擇性中繼資料項目。 `LogicalName` 會對應至 `/resource` 參數 (Switch) 的 `identifier` 參數 (Parameter)，而 `Access` 會對應至 `accessibility-modifier` 參數 (Parameter)。 如需詳細資訊，請參閱 [-resource (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option)。 |
| `ResponseFiles` | 選擇性的 `String` 參數。<br /><br /> 指定包含適用於此工作之命令的回應檔。 如需詳細資訊，請參閱 [@ (指定回應檔)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option)。 |
| `Sources` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定一或多個 c # 原始檔。 |
| `TargetType` | 選擇性的 `String` 參數。<br /><br /> 指定輸出檔的檔案格式。 此參數的值如下：`library` (可建立程式碼程式庫)、`exe` (可建立主控台應用程式)、`module` (可建立模組) 或 `winexe` (可建立 Windows 程式)。 預設值是 `library`。 如需詳細資訊，請參閱 [-target (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option)。 |
| `TreatWarningsAsErrors` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即會將所有警告視為錯誤。 如需詳細資訊，請參閱 [-warnaserror (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option)。 |
| `UseHostCompilerIfAvailable` | 選擇性的 `Boolean` 參數。<br /><br /> 如果有的話，即會指示工作來使用同處理序編譯器物件。 僅 Visual Studio 使用。 |
| `Utf8Output` | 選擇性的 `Boolean` 參數。<br /><br /> 使用 UTF-8 編碼記錄編譯器輸出。 如需詳細資訊，請參閱 [-utf8output (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option)。 |
| `WarningLevel` | 選擇性的 `Int32` 參數。<br /><br /> 指定要針對編譯器顯示的警告層級。 如需詳細資訊，請參閱 [-警告 (c # 編譯器選項) ](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option)。 |
| `WarningsAsErrors` | 選擇性的 `String` 參數。<br /><br /> 指定要視為錯誤的警告清單。 如需詳細資訊，請參閱 [-warnaserror (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option)。<br /><br /> 此參數會覆寫 `TreatWarningsAsErrors` 參數。 |
| `WarningsNotAsErrors` | 選擇性的 `String` 參數。<br /><br /> 指定不要視為錯誤的警告清單。 如需詳細資訊，請參閱 [-warnaserror (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option)。<br /><br /> 唯有將 `TreatWarningsAsErrors` 參數設為 `true` 時，此參數才有用。 |
| `Win32Icon` | 選擇性的 `String` 參數。<br /><br /> 在組件中插入 *.ico* 檔案，讓輸出檔在 [檔案總管] 中具有所需的外觀。 如需詳細資訊，請參閱 [-win32icon (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option)。 |
| `Win32Manifest` | 選擇性的 `String` 參數。<br /><br /> 指定要包含的 Win32 資訊清單。 |
| `Win32Resource` | 選擇性的 `String` 參數。<br /><br /> 將 Win32 資源 (*.res*) 檔案插入輸出檔中。 如需詳細資訊，請參閱 [-win32res (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option)。 |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>範例

下列範例會使用 `Csc` 工作，在 `Compile` 項目集合中從原始程式檔編譯可執行檔。

```xml
<CSC
    Sources="@(Compile)"
    OutputAssembly="$(AppName).exe"
    EmitDebugInformation="true" />
```

## <a name="see-also"></a>另請參閱

- [工作參考](../msbuild/msbuild-task-reference.md)
- [工作](../msbuild/msbuild-tasks.md)
