---
title: 環境節點屬性、選項頁
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio], controlling Tools Options
- Tools Options settings, Environment node properties
ms.assetid: 26dca41f-91fc-4ca7-9103-3da402baa1d5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79ddd62df2afd5052d3ef1ecc0753d3f8ba6cf3a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708325"
---
# <a name="options-page-environment-node-properties"></a>環境節點屬性、選項頁

本文描述與 [選項] 對話方塊 [環境] 分類 `DTE.Properties("Environment", <Property Page>)` 建立關聯的頁面 (或屬性集合)。 每一小節的標題就是用來存取屬性集合的呼叫，而每一小節中的表格會列出集合中的屬性。

## <a name="general"></a>一般

`DTE.Properties("Environment", "General")`

|屬性項目名稱|值|說明|
| - |-----------|-----------------|
|ShowStatusBar|Get/Set (布林值)|決定狀態列是否為可見。|
|WindowMenuContainsNItems|Get/Set (短整數)|決定 Windows 功能表底部包含文件視窗的方式。|
|MRUListContainsNItems|Get/Set (短整數)|決定 [最近使用] 子功能表中顯示的檔案數目。|
|Animations|Get/Set (布林值)|決定整合式開發環境 (IDE) 是否在狀態列中使用動畫。|
|AnimationSpeed|Get/Set (短整數)||
|AutoAdjustExperience|Get/Set (布林值)|自動根據用戶端效能調整視覺效果。|
|RichClientExperienceOptions|Get/Set (列舉)|透過 <xref:EnvDTE100.vsRichClientExperienceOptions> 中的值提供豐富的用戶端視覺效果。|
|CloseButtonActiveTabOnly|Get/Set (布林值)|決定是否只在使用中的索引標籤上顯示 [關閉] 按鈕。|
|AutohidePinActiveTabOnly|Get/Set (布林值)|決定 [自動隱藏] 按鈕是否只會影響使用中的索引標籤。|

## <a name="add-inmacros-security"></a>增益集/巨集安全性

`DTE.Properties("Environment", "AddinMacrosSecurity")`

|屬性項目名稱|值|說明|
| - |-----------|-----------------|
|MacrosEnabled|Get/Set (布林值)|允許執行巨集。|
|AddinsEnabled|Get/Set (布林值)|允許載入增益集。|
|LoadAddinsFromTheWeb|Get/Set (布林值)|允許從網路上的 URL 載入增益集。|

## <a name="documents"></a>文件

`DTE.Properties("Environment", "Documents")`

|屬性項目名稱|值|說明|
| - |-----------|-----------------|
|ReuseSavedActiveDocWindow|Get/Set (布林值)|決定如果已儲存目前文件，開啟新檔案時是否要重複使用目前的文件視窗。 `false` 表示每一個文件都要在新的文件視窗中開啟。|
|DetectFileChangesOutsideIDE|Get/Set (布林值)|決定當作業系統通知 IDE 磁碟上的檔案已做修改時，環境是否自動重新載入在 IDE 中開啟的檔案。|
|AutoloadExternalChanges|Get/Set (布林值)|決定在偵測到開啟的文件有做外部修改時，如果並沒有修改開啟的文件，是否要自動重新載入修改的檔案。 如果開啟的文件有做修改，而且這個屬性為 `true`，則 IDE 提示時會假設這個屬性為 `false`。|
|InitializeOpenFileFromCurrentDocument|Get/Set (布林值)|決定 <xref:EnvDTE.DTEClass.OpenFile%2A> 命令是從最後一個使用中文件，還是從您最後開啟檔案的位置，來植入目錄和檔案名稱。|
|MiscFilesProjectSavesLastNItems|Get/Set (短整數)|決定其他檔案專案所記錄的檔案數目。 如此一來，當您下次使用 IDE 時，就可以看見您最近在磁碟上以其他檔案方式開啟的檔案。|
|ShowMiscFilesProject|Get/Set (布林值)|決定是否顯示其他檔案專案。|
|CheckForConsisentLineEndings|Get/Set (布林值)|在檔案載入時，檢查行尾結束符號是否一致。|
|SaveDocsAsUnicodeWhenDataLoss|Get/Set (布林值)|無法以字碼頁儲存資料時，將文件儲存為 Unicode。|
|DontShowGlobalUndoChangeLossDialog|Get/Set (布林值)|全域復原要修改其他已編輯的檔案時顯示警告。|
|AllowEditingReadOnlyFiles|Get/Set (布林值)|允許編輯唯讀檔案，但是在嘗試儲存檔案時顯示警告。|
|DocumentDockPreference|Get/Set (列舉)|<xref:EnvDTE100.vsDocumentDockPreferenceOptions>. 放置在索引標籤中適合插入已開啟文件的位置。|

## <a name="extension-manager"></a>擴充管理員

`DTE.Properties("Environment", "ExtensionManager")`

|屬性項目名稱|值|說明|
| - |-----------|-----------------|
|EnableAdminExtensions|Get/Set (布林值)|以系統管理員認證執行 Visual Studio 時，載入個別使用者的擴充功能。 變更這個值之後，必須重新啟動 Visual Studio。|
|EnableOnline|Get/Set (布林值)|允許存取 Visual Studio Marketplace 中的擴充功能。|
|AutomaticallyCheckForUpdates|Get/Set (布林值)|自動檢查已安裝擴充功能的更新。|

## <a name="find-and-replace"></a>尋找和取代

`DTE.Properties("Environment", "FindAndReplace")`

|屬性項目名稱|值|說明|
| - |-----------|-----------------|
|ShowWarningMessages|Get/Set (布林值)|顯示警告訊息。|
|InitializeFromEditor|Get/Set (布林值)|以編輯器中的文字自動填入 [尋找目標] 方塊。|
|ShowMessageBoxes|Get/Set (布林值)|顯示告知性訊息。|
|HideWindowsAfterMatchFromQuickFindReplace|Get/Set (布林值)|使用 [快速尋找] 或 [快速取代] 找到符合的項目之後，隱藏 [尋找和取代] 視窗。|

## <a name="import-and-export-settings"></a>匯入和匯出設定

`DTE.Properties("Environment", "Import and Export Settings")`

|屬性項目名稱|值|說明|
| - |-----------|-----------------|
|TrackTeamSettings|Get/Set (布林值)|使用 TeamSettingsFile 所指定檔案中的設定。|
|TeamSettingsFile|Get/Set (字串)|具有小組設定之檔案的名稱。|
|AutoSaveFile|Get/Set (字串)|自動儲存使用者設定之檔案的名稱。|

## <a name="international-settings"></a>國際設定

`DTE.Properties("Environment", "International")`

|屬性項目名稱|值|說明|
| - |-----------|-----------------|
|語言|Get/Set (字串)|Visual Studio 目前語言的 LCID 值。|

## <a name="keyboard"></a>鍵盤

`DTE.Properties("Environment", "Keyboard")`

|屬性項目名稱|值|說明|
| - |-----------|-----------------|
|配置|Get/Set (字串)|傳回包含內建配置的字串、包含所載入之 .vsk 檔完整路徑的字串，如果沒有載入 .vsk 檔，則傳回 "(Default)"。|

## <a name="projects-and-solution"></a>專案和方案

`DTE.Properties("Environment", "ProjectsAndSolution")`

|屬性項目名稱|值|說明|
| - |-----------|-----------------|
|OnRunOrPreview|Get/Set (字串)|決定 IDE 是否先將一切存檔，然後再預覽或執行所建置的專案。|
|ProjectsLocation|Get/Set (字串)|決定 [新增專案] 對話方塊儲存新專案的預設目錄。|
|ShowOutputWindowBeforeBuild|Get/Set (布林值)|決定是否在開始組建時顯示 [輸出] 視窗。|
|ShowTaskListAfterBuild|Get/Set (布林值)|決定當組建完成但建置作業失敗時，是否顯示 [工作清單]。|
|TrackFileSelectionInExplorer|Get/Set (布林值)|決定是否在方案總管中追蹤目前項目。|
|AlwaysShowSolutionNode|Get/Set (布林值)|決定是否顯示方案節點。|
|OnlySaveStartupProjectsAndDependencies|Get/Set (布林值)|決定儲存作業是否只限於啟始專案及其相依檔案。|
|ShowAdvancedBuildConfigurations|Get/Set (布林值)|決定是否顯示進階組建組態。|
|ConcurrentBuilds|Get/Set (字串)|決定可發生之平行專案建置的最大數目。|
|SaveNewProjects|Get/Set (布林值)|決定新專案建立之後是否自動儲存。|
|PromptForRenameSymbol|Get/Set (布林值)|指定是否在重新命名檔案時提示符號重新命名。|
|OnRunWhenErrors|Get/Set (列舉)|指定組建完成但發生錯誤時，在執行上的行為。|
|OnRunWhenOutOfDate|Get/Set (列舉)|指定專案過期時，在執行上的行為。|
|ProjectTemplatesLocation|Get/Set (字串)|包含使用者專案範本的目錄。|
|ProjectItemTemplatesLocation|Get/Set (字串)|包含使用者項目範本的目錄。|
|DefaultBehaviorForStartupProjects|Get/Set (字串)||
|MSBuildOutputVerbosity|Get/Set (字串)|指定組建輸出的詳細等級。|

## <a name="startup"></a>啟動

`DTE.Properties("Environment", "Startup")`

::: moniker range="vs-2017"

|屬性項目名稱|值|說明|
| - |-----------|-----------------|
|OnStartUp|Get/Set (列舉)|從 <xref:EnvDTE.vsStartUp> 啟動時所採取的動作，值為 0 到 5：<br /><br /> -   0：開啟首頁<br />-   1：載入上次載入的方案<br />-   2：顯示 [開啟專案] 對話方塊<br />-   3：顯示 [新增專案] 對話方塊<br />-   4：顯示空白環境<br />-   5：顯示起始畫面|
|StartPageRSSUrl|Get/Set (字串)|啟動時所使用之 RSS 摘要的 URL。|
|StartPageRefreshDownloadedContent|Get/Set (布林值)|每隔 StartPageRefreshInterval 中所指定的間隔之後，重新整理起始頁。|
|StartPageRefreshInterval|Get/Set (短整數)|重新整理起始頁的間隔，以分鐘為單位。|

::: moniker-end

::: moniker range=">=vs-2019"

|屬性項目名稱|值|說明|
| - |-----------|-----------------|
|OnStartUp|Get/Set (列舉)|從 <xref:EnvDTE.vsStartUp> 啟動時所採取的動作。|

::: moniker-end

## <a name="tasklist"></a>TaskList

`DTE.Properties("Environment", "TaskList")`

|屬性項目名稱|值|說明|
| - |-----------|-----------------|
|ConfirmTaskDeletion|Get/Set (布林值)|指定在刪除 [工作清單] 中的工作時，是否顯示確認方塊。|
|WarnOnAddingHiddenItem|Get/Set (布林值)|指定加入不會顯示的使用者工作時，是否對您發出警告。|
|DontShowFilePaths|Get/Set (布林值)|指定是否在 [工作清單] 中顯示完整檔案路徑。|
|CommentTokens|SafeArray|傳回註解語彙基元值的 SafeArray。 各有各的欄位、`Name` (字串) 和 `Priority` (<xref:EnvDTE.vsTaskPriority>、高、中或低)。|

## <a name="web-browser"></a>網頁瀏覽器

`DTE.Properties("Environment", "WebBrowser")`

|屬性項目名稱|值|說明|
| - |-----------|-----------------|
|HomePage|Get/Set (字串)|代表首頁 URL。|
|SearchPage|Get/Set (字串)|代表搜尋網頁 URL。|
|ViewSourceIn|Get/Set (列舉)|<xref:EnvDTE.vsBrowserViewSource> (原始檔、設計、外部)。|
|ViewSourceExternalProgram|Get/Set (字串)|外部來源檢視器的路徑。|

## <a name="see-also"></a>另請參閱

- [控制選項設定](https://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)
- [在選項頁中決定屬性項目的名稱](https://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)
- [字型和色彩節點屬性、選項頁面](../../ide/reference/options-page-fonts-and-colors-node-properties.md)
- [文字編輯器節點屬性、選項頁面](../../ide/reference/options-page-text-editor-node-properties.md)
- [環境選項對話方塊](../../ide/reference/environment-options-dialog-box.md)