---
title: MSBuild 工作參考 | Microsoft Docs
description: 瞭解 MSBuild 隨附的工作，這些工作會提供在組建程式期間執行的程式碼。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f26c3c1b8256597c795fa8bcd815fd605f895fa5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878379"
---
# <a name="msbuild-task-reference"></a>MSBuild 工作參考

提供在建置流程期間執行之程式碼的工作。 下列清單中的工作包含在 MSBuild 中。 當您安裝 c + + 工作負載時，可以使用其他工作來建立 c + + 專案。 如需詳細資訊，請參閱 [c + +](../msbuild/msbuild-tasks-specific-to-visual-cpp.md)工作。

除了本節中主題所列的參數之外，每個工作也會有下列參數：

| 參數 | Description |
|-------------------| - |
| `Condition` | 選擇性的 `String` 參數。<br /><br /> `Boolean`MSBuild 引擎用來判斷是否會執行此工作的運算式。 如需 MSBuild 所支援條件的詳細資訊，請參閱 [條件](../msbuild/msbuild-conditions.md)。 |
| `ContinueOnError` | 選擇性參數。 可包含一或多個下列值：<br /><br /> -   **WarnAndContinue** 或 **true**。 當工作失敗時， [目標](../msbuild/target-element-msbuild.md) 專案和組建中的後續工作會繼續執行，並將工作中的所有錯誤視為警告。<br />-   **ErrorAndContinue**。 當工作失敗時，`Target` 項目中的後續工作與組建都會繼續執行，並將來自工作的所有錯誤視為錯誤。<br />-   **ErrorAndStop** 或 **false** (預設) 。 當工作失敗時，就不會執行 `Target` 項目中的其餘工作和組建，並將整個 `Target` 項目與組建視為失敗。<br /><br /> 只有 4.5 版之前的 .NET Framework 版本支援 `true` 和 `false` 值。<br /><br /> 如需詳細資訊，請參閱[如何：忽略工作中的錯誤](../msbuild/how-to-ignore-errors-in-tasks.md)。 |

## <a name="in-this-section"></a>本節內容

- [Task 基底類別](../msbuild/task-base-class.md)

 將數個參數新增至從 <xref:Microsoft.Build.Utilities.Task> 類別衍生的工作。 不適合直接使用。

- [TaskExtension 基底類別](../msbuild/taskextension-base-class.md)

 將數個參數新增至從 <xref:Microsoft.Build.Tasks.TaskExtension> 類別衍生的工作。 不適合直接使用。

- [ToolTaskExtension 基底類別](../msbuild/tooltaskextension-base-class.md)

 將數個參數新增至從 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 類別衍生的工作。 不適合直接使用。

- [AL (組件連結器) 工作](../msbuild/al-assembly-linker-task.md)

 從一或多個模組或資源檔的檔案中，建立包含資訊清單的組件。

- [AspNetCompiler 工作](../msbuild/aspnetcompiler-task.md)

 包裝 *aspnet_compiler.exe*，此為預先編譯 ASP.NET 應用程式的公用程式。

- [AssignCulture 工作](../msbuild/assignculture-task.md)

 將文化特性識別項指派給項目。

- [AssignProjectConfiguration 工作](../msbuild/assignprojectconfiguration-task.md)

 接受組態字串清單，並將它們指派給指定的專案。

- [AssignTargetPath 工作](../msbuild/assigntargetpath-task.md)

 接受檔案清單，並加入 `<TargetPath>` 屬性 (如果尚未指定)。

- [CallTarget 工作](../msbuild/calltarget-task.md)

 叫用專案檔中的目標。

- [CombinePath 工作](../msbuild/combinepath-task.md)

 將指定的路徑結合成單一路徑。

- [ConvertToAbsolutePath 工作](../msbuild/converttoabsolutepath-task.md)

 將相對路徑或參考轉換為絕對路徑。

- [Copy 工作](../msbuild/copy-task.md)

 將檔案複製到新位置。

- [CreateCSharpManifestResourceName 工作](../msbuild/createcsharpmanifestresourcename-task.md)

 從給定的 *.resx* 檔案名或其他資源，建立 c # 樣式的資訊清單名稱。

- [CreateItem 工作](../msbuild/createitem-task.md)

 從輸入項目填入項目集合，以允許將項目從某一個清單複製到另一個。

- [CreateProperty 工作](../msbuild/createproperty-task.md)

 從輸入值填入屬性，以允許將值從某一個屬性或字串複製到另一個。

- [CreateVisualBasicManifestResourceName 工作](../msbuild/createvisualbasicmanifestresourcename-task.md)

 從給定的 *.resx* 檔案名或其他資源建立 Visual Basic 樣式的資訊清單名稱。

- [Csc 工作](../msbuild/csc-task.md)

 叫用 Visual C# 編譯器來產生可執行檔、動態連結程式庫或程式碼模組。

- [Delete 工作](../msbuild/delete-task.md)

 刪除指定的檔案。

- [DownloadFile 工作](../msbuild/downloadfile-task.md)

 將檔案下載至指定的位置。

- [Error 工作](../msbuild/error-task.md)

 停止組建，並根據評估的條件陳述式來記錄錯誤。

- [Exec 工作](../msbuild/exec-task.md)

 使用指定的引數來執行指定的程式或命令。

- [FindAppConfigFile 工作](../msbuild/findappconfigfile-task.md)

 在提供的清單中尋找 *app.config* 檔案（如果有的話）。

- [FindInList 工作](../msbuild/findinlist-task.md)

 在指定的清單中尋找具有相符項目規格的項目。

- [FindUnderPath 工作](../msbuild/findunderpath-task.md)

 判斷指定項目集合中的哪些項目存在於指定的資料夾及其所有子資料夾中。

- [FormatUrl 工作](../msbuild/formaturl-task.md)

 將 URL 轉換為正確的 URL 格式。

- [FormatVersion 工作](../msbuild/formatversion-task.md)

 將修訂編號附加至版本號碼。

- [GenerateApplicationManifest 工作](../msbuild/generateapplicationmanifest-task.md)

 產生 ClickOnce 應用程式資訊清單或原生資訊清單。

- [GenerateBootstrapper 工作](../msbuild/generatebootstrapper-task.md)

 提供自動化方式來偵測、下載及安裝應用程式及其必要條件。

- [GenerateDeploymentManifest 工作](../msbuild/generatedeploymentmanifest-task.md)

 產生 ClickOnce 部署資訊清單。

- [GenerateResource 工作](../msbuild/generateresource-task.md)

 將 *.txt* 和 *.resx* 檔案轉換為通用語言執行階段二進位 *.resources* 檔案。

- [GenerateTrustInfo 工作](../msbuild/generatetrustinfo-task.md)

 從基底資訊清單，以及從 `TargetZone` 與 `ExcludedPermissions` 參數產生應用程式信任。

- [GetAssemblyIdentity 工作](../msbuild/getassemblyidentity-task.md)

 從指定的檔案擷取組件識別，並輸出識別資訊。

- [GetFileHash 工作](../msbuild/getfilehash-task.md)

 計算檔案或一組檔案內容的總和檢查碼。

- [GetFrameworkPath 工作](../msbuild/getframeworkpath-task.md)

 擷取 .NET Framework 組件的路徑。

- [GetFrameworkSdkPath 工作](../msbuild/getframeworksdkpath-task.md)

 抓取 Windows 軟體開發套件 (SDK) 的路徑。

- [GetReferenceAssemblyPaths 工作](../msbuild/getreferenceassemblypaths-task.md)

 傳回各種架構的參考組件路徑。

- [LC 工作](../msbuild/lc-task.md)

 從 *.licx* 檔案產生 *.license* 檔案。

- [MakeDir 工作](../msbuild/makedir-task.md)

 建立目錄，以及任何父目錄 (如有必要)。

- [Message 工作](../msbuild/message-task.md)

 在建置期間記錄訊息。

- [Move 工作](../msbuild/move-task.md)

 將檔案移到新位置。

- [MSBuild 工作](../msbuild/msbuild-task.md)

 從另一個 MSBuild 專案建立 MSBuild 專案。

- [ReadLinesFromFile 工作](../msbuild/readlinesfromfile-task.md)

 從文字檔讀取項目清單。

- [RegisterAssembly 工作](../msbuild/registerassembly-task.md)

 讀取指定組件內的中繼資料，並將必要的項目加入至登錄。

- [RemoveDir 工作](../msbuild/removedir-task.md)

 移除指定的目錄及其所有檔案和子目錄。

- [RemoveDuplicates 工作](../msbuild/removeduplicates-task.md)

 從指定的項目集合中移除重複項目。

- [RequiresFramework35SP1Assembly 工作](../msbuild/requiresframework35sp1assembly-task.md)

 判斷應用程式是否需要 .NET Framework 3.5 SP1。

- ResGen 工作

 已過時。 使用 [GenerateResource 工作](../msbuild/generateresource-task.md)，將 *.txt* 和 *.resx* 檔案轉換為通用語言執行階段二進位 *.resources* 檔案，反之亦然。

- [ResolveAssemblyReference 工作](../msbuild/resolveassemblyreference-task.md)

 判斷相依於指定組件的所有組件。

- [ResolveComReference 工作](../msbuild/resolvecomreference-task.md)

 取得一或多個類型程式庫名稱的清單或 *.tlb* 檔案，並將那些類型程式庫解析至磁碟上的位置。

- [ResolveKeySource 工作](../msbuild/resolvekeysource-task.md)

 決定強式名稱金鑰來源

- [ResolveManifestFiles 工作](../msbuild/resolvemanifestfiles-task.md)

 將建置流程中的下列項目解析為檔案，以產生資訊清單：建置的項目、相依性、附屬項目、內容、偵錯符號和文件。

- [ResolveNativeReference 工作](../msbuild/resolvenativereference-task.md)

 解析原生參考。

- [ResolveNonMSBuildProjectOutput 工作](../msbuild/resolvenonmsbuildprojectoutput-task.md)

 決定非 MSBuild 專案參考的輸出檔。

- [SGen 工作](../msbuild/sgen-task.md)

 針對指定組件中的型別建立 XML 序列化組件。

- [SignFile 工作](../msbuild/signfile-task.md)

 使用指定的憑證簽署指定的檔案。

- [Touch 工作](../msbuild/touch-task.md)

 設定檔案的存取和修改時間。

- [UnregisterAssembly 工作](../msbuild/unregisterassembly-task.md)

 針對 COM Interop 用途取消註冊指定的組件。

- [Unzip 工作](../msbuild/unzip-task.md)

 將 *.zip* 封存解壓縮至指定的位置。

- [UpdateManifest 工作](../msbuild/updatemanifest-task.md)

 更新資訊清單中選取的屬性，並重新簽署。

- [Vbc 工作](../msbuild/vbc-task.md)

 叫用 Visual Basic 編譯器來產生可執行檔、動態連結程式庫或程式碼模組。

- [VerifyFileHash 工作](../msbuild/verifyfilehash-task.md)

 驗證檔案是否符合預期的檔案雜湊。

- [Warning 工作](../msbuild/warning-task.md)

 在建置期間，根據評估的條件陳述式來記錄警告。

- [WriteCodeFragment 工作](../msbuild/writecodefragment-task.md)

 使用指定產生的程式碼片段來產生暫存程式碼檔。 不會刪除該檔案。

- [WriteLinesToFile 工作](../msbuild/writelinestofile-task.md)

 將指定的項目寫入指定的文字檔。

- [XmlPeek 工作](../msbuild/xmlpeek-task.md)

 將 XPath 查詢所指定的值從 XML 檔案傳回。

- [XmlPoke 工作](../msbuild/xmlpoke-task.md)

 將 XPath 查詢所指定的值設定至 XML 檔案。

- [XslTransformation 工作](../msbuild/xsltransformation-task.md)

 使用「可延伸樣式表語言轉換」(XSLT) 或編譯的 XSLT 轉換 XML 輸入，並輸出到輸出裝置或檔案。

- [ZipDirectory 工作](../msbuild/zipdirectory-task.md)

 從目錄的內容建立 *.zip* 封存。

## <a name="see-also"></a>另請參閱

- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [工作撰寫](../msbuild/task-writing.md)
- [工作](../msbuild/msbuild-tasks.md)
