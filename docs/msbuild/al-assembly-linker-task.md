---
title: AL (組件連結器) 工作 | Microsoft Docs
description: 使用 MSBuild 元件連結器 (AL) 工作來包裝 AL.exe，這是與 Windows 軟體開發套件一起散發的工具。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AL
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- AL task [MSBuild]
- MSBuild, AL task
ms.assetid: 2ddefbf2-5662-4d55-99a6-ac383bf44560
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3d99c33a74512b380d7b5260d5b7e747c6a39e41
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923867"
---
# <a name="al-assembly-linker-task"></a>AL (組件連結器) 工作

AL 工作會包裝 *AL.exe*，這是隨 WINDOWS 軟體開發套件 (SDK) 散發的工具。 這個組件連結器工具可用來從一或多個屬於模組或資源檔的檔案中，建立包含資訊清單的組件。 編譯器和開發環境可能已經提供這些功能，因此通常不需直接使用此工作。 如果開發人員需要從多個元件檔案建立單一組件 (例如，可能是從混合式語言開發中產生的那些)，則組件連結器就非常實用。 此工作不能將多個模組合併成單一組件檔案；您仍需依序散發和提供個別的模組，才能讓產生的組件正確載入。 如需 AL.exe 的詳細資訊，請參閱 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker)。

## <a name="parameters"></a>參數

 下表說明 `AL` 工作的參數。

| 參數 | Description |
|---------------------| - |
| `AlgorithmID` | 選擇性的 `String` 參數。<br /><br /> 指定雜湊多檔案組件中所有檔案的演算法，但包含組件資訊清單的檔案除外。 如需詳細資訊，請參閱 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中 `/algid` 選項的說明文件。 |
| `BaseAddress` | 選擇性的 `String` 參數。<br /><br /> 指定在執行期間將 DLL 載入使用者電腦上的目標位址。 如果您指定 DLL 的基底位址，而不是讓作業系統重新找出處理序空間中的 DLL，應用程式載入的速度會更快。 此參數對應至 /base[address](/dotnet/framework/tools/al-exe-assembly-linker)。 |
| `CompanyName` | 選擇性的 `String` 參數。<br /><br /> 為組件中的 [`Company`] 欄位指定字串。 如需詳細資訊，請參閱 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中 `/comp[any]` 選項的說明文件。 |
| `Configuration` | 選擇性的 `String` 參數。<br /><br /> 為組件中的 [`Configuration`] 欄位指定字串。 如需詳細資訊，請參閱 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中 `/config[uration]` 選項的說明文件。 |
| `Copyright` | 選擇性的 `String` 參數。<br /><br /> 為組件中的 [`Copyright`] 欄位指定字串。 如需詳細資訊，請參閱 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中 `/copy[right]` 選項的說明文件。 |
| `Culture` | 選擇性的 `String` 參數。<br /><br /> 指定與組件相關聯的文化特性字串。 如需詳細資訊，請參閱 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中 `/c[ulture]` 選項的說明文件。 |
| `DelaySign` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，只會在組件中放置公開金鑰；如果是 `false`，即會完整簽署組件。 如需詳細資訊，請參閱 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中 `/delay[sign]` 選項的說明文件。 |
| `Description` | 選擇性的 `String` 參數。<br /><br /> 為組件中的 [`Description`] 欄位指定字串。 如需詳細資訊，請參閱 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中 `/descr[iption]` 選項的說明文件。 |
| `EmbedResources` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 在含有組件資訊清單的映像中嵌入指定的資源。 此工作會將資源檔的內容複製到映像。 傳遞給這個參數的項目可能具有已附加到它們的選擇性中繼資料，稱為 `LogicalName` 和 `Access`。 `LogicalName` 中繼資料可用來指定資源的內部識別項。  您可以將 `Access` 中繼資料設為 `private`，以便讓其他組件無法看見資源。 如需詳細資訊，請參閱 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中 `/embed[resource]` 選項的說明文件。 |
| `EvidenceFile` | 選擇性的 `String` 參數。<br /><br /> 使用 `Security.Evidence` 的資源名稱，將指定的檔案嵌入組件中。<br /><br /> `Security.Evidence` 無法用於一般資源。 此參數對應到 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中的 `/e[vidence]` 選項。 |
| `ExitCode` | 選擇性 `Int32` 輸出唯讀參數。<br /><br /> 指定已執行命令提供的結束代碼。 |
| `FileVersion` | 選擇性的 `String` 參數。<br /><br /> 為組件中的 [`File Version`] 欄位指定字串。 如需詳細資訊，請參閱 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中 `/fileversion` 選項的說明文件。 |
| `Flags` | 選擇性的 `String` 參數。<br /><br /> 為組件中的 [`Flags`] 欄位指定值。 如需詳細資訊，請參閱 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中 `/flags` 選項的說明文件。 |
| `GenerateFullPaths` | 選擇性的 `Boolean` 參數。<br /><br /> 讓工作使用錯誤訊息中所報告之任何檔案的絕對路徑。 此參數對應到 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中的 `/fullpaths` 選項。 |
| `KeyContainer` | 選擇性的 `String` 參數。<br /><br /> 指定保留金鑰組的容器。 這樣會藉由將公開金鑰插入組件資訊清單中的方式簽署組件 (為它指定強式名稱)。 然後工作將會使用私密金鑰簽署最終組件。 如需詳細資訊，請參閱 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中 `/keyn[ame]` 選項的說明文件。 |
| `KeyFile` | 選擇性的 `String` 參數。<br /><br /> 指定包含金鑰組或只有公開金鑰的檔案以簽署組件。 編譯器會將公開金鑰插入組件資訊清單中，然後使用私密金鑰簽署最終組件。 如需詳細資訊，請參閱 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中 `/keyf[ile]` 選項的說明文件。 |
| `LinkResources` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 將指定的資源檔連結至組件。 資源會變成組件的一部分，但不會複製檔案。 傳遞給這個參數的項目可能具有已附加到它們的選擇性中繼資料，稱為 `LogicalName`、`Target` 及 `Access`。 `LogicalName` 中繼資料可用來指定資源的內部識別項。 `Target` 中繼資料可以指定工作要將檔案複製到其中的路徑和檔案名稱，之後它會將這個新檔案編譯成組件。 您可以將 `Access` 中繼資料設為 `private`，以便讓其他組件無法看見資源。 如需詳細資訊，請參閱 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中 `/link[resource]` 選項的說明文件。 |
| `MainEntryPoint` | 選擇性的 `String` 參數。<br /><br /> 指定將模組轉換成可執行檔時，用來作為進入點之方法的完整名稱 (*class.method*)。 此參數對應到 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中的 `/main` 選項。 |
| `OutputAssembly` | 必要的 <xref:Microsoft.Build.Framework.ITaskItem> 輸出參數。<br /><br /> 指定此工作產生的檔案名稱。 此參數對應到 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中的 `/out` 選項。 |
| `Platform` | 選擇性的 `String` 參數。<br /><br /> 限制可以執行這個程式碼的平台，這個平台必須為下列其中之一：`x86`、`Itanium`、`x64` 或 `anycpu`。 預設為 `anycpu`。 此參數對應到 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中的 `/platform` 選項。 |
| `ProductName` | 選擇性的 `String` 參數。<br /><br /> 為組件中的 [`Product`] 欄位指定字串。 如需詳細資訊，請參閱 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中 `/prod[uct]` 選項的說明文件。 |
| `ProductVersion` | 選擇性的 `String` 參數。<br /><br /> 為組件中的 [`ProductVersion`] 欄位指定字串。 如需詳細資訊，請參閱 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中 `/productv[ersion]` 選項的說明文件。 |
| `ResponseFiles` | 選擇性的 `String[]` 參數。<br /><br /> 指定包含要傳遞至組件連結器之其他選項的回應檔。 |
| `SdkToolsPath` | 選擇性的 `String` 參數。<br /><br /> 指定 SDK 工具 (例如 resgen.exe) 的路徑。 |
| `SourceModules` | 選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 一或多個要編譯到組件的模組。 模組將列在所產生組件的資訊清單中，且仍需依序散發和提供，才能載入組件。 傳遞到此參數的項目可能具有名為 `Target` 的其他中繼資料，以指定工作要將檔案複製到其中的路徑和檔案名稱，之後它會將這個新檔案編譯成組件。 如需詳細資訊，請參閱 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 的說明文件。 此參數對應至未使用特定參數傳遞至 *Al.exe* 的模組清單。 |
| `TargetType` | 選擇性的 `String` 參數。<br /><br /> 指定輸出檔的檔案格式：`library` (程式碼程式庫)、`exe` (主控台應用程式) 或 `win` (Windows 應用程式)。 預設為 `library`。 此參數對應到 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中的 `/t[arget]` 選項。 |
| `TemplateFile` | 選擇性的 `String` 參數。<br /><br /> 指定要從其中繼承所有組件中繼資料的組件，但不包括 [文化特性] 欄位。 指定的組件必須具有強式名稱。<br /><br /> 使用 `TemplateFile` 參數建立的組件會是附屬組件。 此參數對應到 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中的 `/template` 選項。 |
| `Timeout` | 選擇性的 `Int32` 參數。<br /><br /> 指定時間量 (以毫秒為單位)，在此時間量之後會終止工作可執行檔。 預設值是 `Int.MaxValue`，表示沒有逾時期間。 |
| `Title` | 選擇性的 `String` 參數。<br /><br /> 為組件中的 [`Title`] 欄位指定字串。 如需詳細資訊，請參閱 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中 `/title` 選項的說明文件。 |
| `ToolPath` | 選擇性的 `String` 參數。<br /><br /> 指定位置，工作會從該位置載入基礎可執行檔 (Al.exe)。 如果未指定此參數，工作會使用 SDK 安裝路徑，對應至執行 MSBuild 的 framework 版本。 |
| `Trademark` | 選擇性的 `String` 參數。<br /><br /> 為組件中的 [`Trademark`] 欄位指定字串。 如需詳細資訊，請參閱 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中 `/trade[mark]` 選項的說明文件。 |
| `Version` | 選擇性的 `String` 參數。<br /><br /> 指定這個組件的版本資訊。 字串格式是 *major.minor.build.revision*。 預設值為 0。 如需詳細資訊，請參閱 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中 `/v[ersion]` 選項的說明文件。 |
| `Win32Icon` | 選擇性的 `String` 參數。<br /><br /> 將 *.ico* 檔案插入組件中。 *.ico* 檔案會讓輸出檔案在檔案總管中以所要的外觀顯示。 此參數對應到 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中的 `/win32icon` 選項。 |
| `Win32Resource` | 選擇性的 `String` 參數。<br /><br /> 將 Win32 資源 (*.res* 檔案) 插入輸出檔案中。 如需詳細資訊，請參閱 [Al.exe (組件連結器)](/dotnet/framework/tools/al-exe-assembly-linker) 中 `/win32res` 選項的說明文件。 |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>範例

 下列範例會使用指定的選項來建立組件。

```xml
<AL
    EmbedResources="@(EmbeddedResource)"
    Culture="%(EmbeddedResource.Culture)"
    TemplateFile="@(IntermediateAssembly)"
    KeyContainer="$(KeyContainerName)"
    KeyFile="$(KeyOriginatorFile)"
    DelaySign="$(DelaySign)"

    OutputAssembly=
       "%(EmbeddedResource.Culture)\$(TargetName).resources.dll">

    <Output TaskParameter="OutputAssembly"
        ItemName="SatelliteAssemblies"/>
</AL>
```

## <a name="see-also"></a>另請參閱

* [工作參考](../msbuild/msbuild-task-reference.md)
* [工作](../msbuild/msbuild-tasks.md)
