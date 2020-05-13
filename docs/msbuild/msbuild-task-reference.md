---
title: MSBuild 工作參考 | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbec3c7c020bae0e94bc16bdb1fe9740a36a93ae
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "78865319"
---
# <a name="msbuild-task-reference"></a>MSBuild 工作參考

提供在建置流程期間執行之程式碼的工作。 MSBuild 中包含以下清單中的任務。 安裝C++工作負荷時，可以使用用於生成C++專案的其他任務。 有關詳細資訊，請參閱[C++任務](../msbuild/msbuild-tasks-specific-to-visual-cpp.md)。

除了本節中主題所列的參數之外，每個工作也會有下列參數：

| 參數 | 描述 |
|-------------------| - |
| `Condition` | 選擇性的 `String` 參數。<br /><br /> MSBuild 引擎用來確定是否執行此任務的`Boolean`運算式。 有關 MSBuild 支援的條件的資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。 |
| `ContinueOnError` | 選擇性參數。 可包含一或多個下列值：<br /><br /> -   **警告並繼續**或**真實**。 當任務失敗時[，Target](../msbuild/target-element-msbuild.md)元素和生成中的後續任務將繼續執行，並且任務中的所有錯誤都被視為警告。<br />-   **錯誤並繼續**。 當工作失敗時，`Target` 項目中的後續工作與組建都會繼續執行，並將來自工作的所有錯誤視為錯誤。<br />-   **錯誤和停止**或**錯誤**（預設值）。 當工作失敗時，就不會執行 `Target` 項目中的其餘工作和組建，並將整個 `Target` 項目與組建視為失敗。<br /><br /> 只有 4.5 版之前的 .NET Framework 版本支援 `true` 和 `false` 值。<br /><br /> 如需詳細資訊，請參閱[如何：忽略工作中的錯誤](../msbuild/how-to-ignore-errors-in-tasks.md)。 |

## <a name="in-this-section"></a>本節內容

- [Task 基底類別](../msbuild/task-base-class.md)

 將數個參數新增至從 <xref:Microsoft.Build.Utilities.Task> 類別衍生的工作。 不打算直接使用。

- [任務擴展基類](../msbuild/taskextension-base-class.md)

 將數個參數新增至從 <xref:Microsoft.Build.Tasks.TaskExtension> 類別衍生的工作。 不打算直接使用。

- [ToolTaskExtension 基底類別](../msbuild/tooltaskextension-base-class.md)

 將數個參數新增至從 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 類別衍生的工作。 不打算直接使用。

- [AL (組件連結器) 工作](../msbuild/al-assembly-linker-task.md)

 從一或多個模組或資源檔的檔案中，建立包含資訊清單的組件。

- [阿斯普網路編譯器任務](../msbuild/aspnetcompiler-task.md)

 包裝 *aspnet_compiler.exe*，此為預先編譯 ASP.NET 應用程式的公用程式。

- [分配文化任務](../msbuild/assignculture-task.md)

 將文化特性識別項指派給項目。

- [分配專案配置任務](../msbuild/assignprojectconfiguration-task.md)

 接受組態字串清單，並將它們指派給指定的專案。

- [分配目標路徑任務](../msbuild/assigntargetpath-task.md)

 接受檔案清單，並加入 `<TargetPath>` 屬性 (如果尚未指定)。

- [呼叫目標任務](../msbuild/calltarget-task.md)

 叫用專案檔中的目標。

- [合併路徑任務](../msbuild/combinepath-task.md)

 將指定的路徑結合成單一路徑。

- [轉換為絕對路徑任務](../msbuild/converttoabsolutepath-task.md)

 將相對路徑或參考轉換為絕對路徑。

- [複製任務](../msbuild/copy-task.md)

 將檔案複製到新位置。

- [創建CSharpManifest資源名稱任務](../msbuild/createcsharpmanifestresourcename-task.md)

 從給定*的 .resx*檔案名或其他資源創建 C#樣式的清單名稱。

- [創建專案工作](../msbuild/createitem-task.md)

 從輸入項目填入項目集合，以允許將項目從某一個清單複製到另一個。

- [CreateProperty 工作](../msbuild/createproperty-task.md)

 從輸入值填入屬性，以允許將值從某一個屬性或字串複製到另一個。

- [創建視覺化基本清單資源名稱任務](../msbuild/createvisualbasicmanifestresourcename-task.md)

 從給定的 *.resx*檔案名或其他資源創建可視基本樣式清單名稱。

- [Csc 工作](../msbuild/csc-task.md)

 叫用 Visual C# 編譯器來產生可執行檔、動態連結程式庫或程式碼模組。

- [刪除任務](../msbuild/delete-task.md)

 刪除指定的檔案。

- [下載檔案任務](../msbuild/downloadfile-task.md)

 將檔案下載至指定的位置。

- [Error 工作](../msbuild/error-task.md)

 停止組建，並根據評估的條件陳述式來記錄錯誤。

- [執行任務](../msbuild/exec-task.md)

 使用指定的引數來執行指定的程式或命令。

- [查找應用設定檔任務](../msbuild/findappconfigfile-task.md)

 在提供的清單中尋找 *app.config* 檔案 (若有的話)。

- [查找清單任務](../msbuild/findinlist-task.md)

 在指定的清單中尋找具有相符項目規格的項目。

- [FindUnderPath 工作](../msbuild/findunderpath-task.md)

 判斷指定項目集合中的哪些項目存在於指定的資料夾及其所有子資料夾中。

- [格式Url任務](../msbuild/formaturl-task.md)

 將 URL 轉換為正確的 URL 格式。

- [格式版本任務](../msbuild/formatversion-task.md)

 將修訂編號附加至版本號碼。

- [生成應用程式清單任務](../msbuild/generateapplicationmanifest-task.md)

 生成 ClickOnce 應用程式清單或本機清單。

- [生成引導器任務](../msbuild/generatebootstrapper-task.md)

 提供自動化方式來偵測、下載及安裝應用程式及其必要條件。

- [GenerateDeploymentManifest 工作](../msbuild/generatedeploymentmanifest-task.md)

 生成 ClickOnce 部署清單。

- [生成資源任務](../msbuild/generateresource-task.md)

 將 *.txt* 和 *.resx* 檔案轉換為通用語言執行階段二進位 *.resources* 檔案。

- [GenerateTrustInfo 工作](../msbuild/generatetrustinfo-task.md)

 從基底資訊清單，以及從 `TargetZone` 與 `ExcludedPermissions` 參數產生應用程式信任。

- [獲取裝配標識任務](../msbuild/getassemblyidentity-task.md)

 從指定的檔案擷取組件識別，並輸出識別資訊。

- [GetFileHash 工作](../msbuild/getfilehash-task.md)

 計算檔案或一組檔案內容的總和檢查碼。

- [獲取框架路徑任務](../msbuild/getframeworkpath-task.md)

 擷取 .NET Framework 組件的路徑。

- [獲取框架SdkPath任務](../msbuild/getframeworksdkpath-task.md)

 檢索到 Windows 軟體發展工具組 （SDK） 的路徑。

- [獲取參考裝配路徑任務](../msbuild/getreferenceassemblypaths-task.md)

 傳回各種架構的參考組件路徑。

- [LC 任務](../msbuild/lc-task.md)

 從 *.licx* 檔案產生 *.license* 檔案。

- [MakeDir 工作](../msbuild/makedir-task.md)

 建立目錄，以及任何父目錄 (如有必要)。

- [消息任務](../msbuild/message-task.md)

 在建置期間記錄訊息。

- [移動任務](../msbuild/move-task.md)

 將檔案移到新位置。

- [MSBuild 工作](../msbuild/msbuild-task.md)

 從另一個 MSBuild 專案生成 MSBuild 專案。

- [從檔任務讀取線](../msbuild/readlinesfromfile-task.md)

 從文字檔讀取項目清單。

- [RegisterAssembly 工作](../msbuild/registerassembly-task.md)

 讀取指定組件內的中繼資料，並將必要的項目加入至登錄。

- [刪除 Dir 任務](../msbuild/removedir-task.md)

 移除指定的目錄及其所有檔案和子目錄。

- [RemoveDuplicates 工作](../msbuild/removeduplicates-task.md)

 從指定的項目集合中移除重複項目。

- [RequiresFramework35SP1Assembly 工作](../msbuild/requiresframework35sp1assembly-task.md)

 判斷應用程式是否需要 .NET Framework 3.5 SP1。

- ResGen 工作

 已過時。 使用 [GenerateResource 工作](../msbuild/generateresource-task.md)，將 *.txt* 和 *.resx* 檔案轉換為通用語言執行階段二進位 *.resources* 檔案，反之亦然。

- [解析裝配參考任務](../msbuild/resolveassemblyreference-task.md)

 判斷相依於指定組件的所有組件。

- [解析通信參考任務](../msbuild/resolvecomreference-task.md)

 取得一或多個類型程式庫名稱的清單或 *.tlb* 檔案，並將那些類型程式庫解析至磁碟上的位置。

- [ResolveKeySource 工作](../msbuild/resolvekeysource-task.md)

 決定強式名稱金鑰來源

- [解析清單檔任務](../msbuild/resolvemanifestfiles-task.md)

 將建置流程中的下列項目解析為檔案，以產生資訊清單：建置的項目、相依性、附屬項目、內容、偵錯符號和文件。

- [ResolveNativeReference 工作](../msbuild/resolvenativereference-task.md)

 解析原生參考。

- [解決NonMS生成專案輸出任務](../msbuild/resolvenonmsbuildprojectoutput-task.md)

 決定非 MSBuild 專案參考的輸出檔。

- [SGen 任務](../msbuild/sgen-task.md)

 針對指定組件中的型別建立 XML 序列化組件。

- [SignFile 工作](../msbuild/signfile-task.md)

 使用指定的憑證簽署指定的檔案。

- [觸摸任務](../msbuild/touch-task.md)

 設定檔案的存取和修改時間。

- [取消註冊裝配任務](../msbuild/unregisterassembly-task.md)

 針對 COM Interop 用途取消註冊指定的組件。

- [解壓縮任務](../msbuild/unzip-task.md)

 將 *.zip* 封存解壓縮至指定的位置。

- [更新清單任務](../msbuild/updatemanifest-task.md)

 更新資訊清單中選取的屬性，並重新簽署。

- [Vbc 任務](../msbuild/vbc-task.md)

 叫用 Visual Basic 編譯器來產生可執行檔、動態連結程式庫或程式碼模組。

- [VerifyFileHash 工作](../msbuild/verifyfilehash-task.md)

 驗證檔案是否符合預期的檔案雜湊。

- [警告任務](../msbuild/warning-task.md)

 在建置期間，根據評估的條件陳述式來記錄警告。

- [編寫代碼碎片任務](../msbuild/writecodefragment-task.md)

 使用指定產生的程式碼片段來產生暫存程式碼檔。 不會刪除該檔案。

- [寫入線到檔任務](../msbuild/writelinestofile-task.md)

 將指定的項目寫入指定的文字檔。

- [XmlPeek 工作](../msbuild/xmlpeek-task.md)

 將 XPath 查詢所指定的值從 XML 檔案傳回。

- [XmlPoke 任務](../msbuild/xmlpoke-task.md)

 將 XPath 查詢所指定的值設定至 XML 檔案。

- [Xsl 轉換任務](../msbuild/xsltransformation-task.md)

 使用「可延伸樣式表語言轉換」**(XSLT) 或編譯的 XSLT 轉換 XML 輸入，並輸出到輸出裝置或檔案。

- [ZipDirectory 任務](../msbuild/zipdirectory-task.md)

 從目錄的內容建立 *.zip* 封存。

## <a name="see-also"></a>另請參閱

- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [任務編寫](../msbuild/task-writing.md)
- [工作](../msbuild/msbuild-tasks.md)
