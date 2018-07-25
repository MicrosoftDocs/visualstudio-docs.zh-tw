---
title: 專案和方案、選項對話方塊
ms.date: 07/14/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
- VS.ToolsOptionsPages.Projects.Locations
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dbd3fe20377cd2aa4954e904fec50702cc9b7120
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2018
ms.locfileid: "34843987"
---
# <a name="projects-and-solutions-page-options-dialog-box"></a>選項對話方塊、專案和方案頁面

設定與專案和解決方案有關的 Visual Studio 行為。 若要存取這些選項，請選取 [工具] > [選項] 來展開 [專案和方案]，然後選取 [一般]。

專案和範本資料夾的預設路徑會透過相同對話方塊中的 [位置] 索引標籤進行設定。

> [!NOTE]
> 視您使用中的設定或版本而定，UI 中的可用選項可能不同於此處所描述的選項。 撰寫本文時，會考慮到 [一般開發設定]。 若要檢視或變更您的設定，請選擇 [工具] 功能表上的 [匯入和匯出設定]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)。

## <a name="general-page"></a>[一般] 頁面

下列選項位於 [一般] 頁面上。

### <a name="always-show-error-list-if-build-finishes-with-errors"></a>建置完成但發生錯誤時一律顯示錯誤清單

只有在無法建置專案時，才在建置完成時開啟 [錯誤清單]。 這樣會顯示在建置過程中發生的錯誤。 清除此選項時，仍然會發生錯誤，但是建置完成時不會開啟視窗。 這個選項預設為啟用。

### <a name="track-active-item-in-solution-explorer"></a>在 [方案總管] 中追蹤使用中的項目

選取此選項時，方案總管會自動開啟並選取使用中的項目。 隨著您使用專案或方案中的不同檔案，或設計工具中的不同元件，選取的項目也會變更。 如果清除這個選項，方案總管中的選取項目就不會自動變更。 這個選項預設為啟用。

### <a name="show-advanced-build-configurations"></a>顯示進階建置組態

選取此選項時，[專案屬性頁] 對話方塊和 [方案屬性頁] 對話方塊就會顯示組建組態選項。 清除此選項時，Visual Basic 與 C# 專案 (包含一或兩個組態偵錯和發行) 的 [專案屬性頁] 對話方塊和 [方案屬性頁] 對話方塊就不會顯示組建組態選項。 如果專案具有使用者定義的組態，就會顯示建置組態選項。

取消選取此選項時，[建置] 功能表上的命令 (例如 [建置方案]、[重建方案] 及 [清除方案]) 會在發行組態上執行，而 [偵錯] 功能表上的命令 (例如 [開始偵錯] 及 [啟動但不偵錯]) 則會在偵錯組態上執行。

### <a name="always-show-solution"></a>一律顯示方案

選取此選項時，IDE 一律會顯示方案以及針對方案執行的所有命令。 清除此選項時，所有專案都會建立為獨立專案；如果方案只包含一個專案，您就不會在 [方案總管] 中看到方案，也不會在 IDE 中看到針對方案執行的命令。

### <a name="save-new-projects-when-created"></a>在建立新專案時予以儲存

選取此選項時，您可以在 [新增專案] 對話方塊中指定專案的位置。 清除此選項時，所有新專案都會建立為暫存專案。 當您使用暫存專案時，可以建立和測試專案，而不需要指定磁碟位置。

### <a name="warn-user-when-the-project-location-is-not-trusted"></a>在專案位置未受信任時警告使用者

如果您嘗試在未受完全信任的位置建立新專案或開啟現有專案 (例如，在 UNC 路徑或 HTTP 路徑上)，則會顯示訊息。 使用此選項，指定每當您在未受完全信任的位置嘗試建立或開啟專案時，是否要顯示訊息。

### <a name="show-output-window-when-build-starts"></a>建置開始時顯示輸出視窗

開始建置解決方案時，自動在 IDE 中顯示[輸出視窗](../../ide/reference/output-window.md)。

### <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>在重新命名檔案時提示符號重新命名

選取此選項時，Visual Studio 會顯示訊息方塊，詢問是否也應重新命名專案中所有對程式碼項目的參考。

### <a name="prompt-before-moving-files-to-a-new-location"></a>將檔案移至新位置前先提示

選取此選項時，在 [方案總管] 中執行檔案的位置變更前，Visual Studio 會顯示確認訊息方塊。

### <a name="reopen-documents-on-solution-load"></a>在解決方案載入時重新開啟文件

**Visual Studio 2017 15.8 版 preview 2 和更新版本**

選取此選項時，會在開啟解決方案時，自動開啟上次關閉此解決方案時處於開啟狀態的文件。

重新開啟特定類型的檔案或設計工具可能會導致方案載入延遲。 如果您不想要還原解決方案先前的內容，請將此選項取消選取以[提升解決方案載入效能](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore)。

## <a name="locations-page"></a>[位置] 頁面

下列選項位於 [位置] 頁面上。

### <a name="projects-location"></a>專案位置

指定 Visual Studio 建立新專案和解決方案資料夾的預設位置。 許多對話方塊也會使用此選項所設定的位置當成資料夾起始點。 例如，[開啟專案] 對話方塊使用此位置當成 [我的專案] 捷徑。

### <a name="user-project-templates-location"></a>使用者專案範本位置

指定 [新增專案] 對話方塊用來建立 [我的範本] 清單的預設位置。 如需詳細資訊，請參閱[如何：尋找並整理範本](../../ide/how-to-locate-and-organize-project-and-item-templates.md)。

### <a name="user-item-templates-location"></a>使用者項目範本位置

指定 [新增新項目] 對話方塊用來建立 [我的範本] 清單的預設位置。 如需詳細資訊，請參閱[如何：尋找並整理範本](../../ide/how-to-locate-and-organize-project-and-item-templates.md)。

## <a name="see-also"></a>另請參閱

- [選項對話方塊、專案和方案、建置並執行](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [選項對話方塊、專案和方案、Web 專案](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
