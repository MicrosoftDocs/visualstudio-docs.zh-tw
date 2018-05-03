---
title: Visual Studio 離線說明文件
ms.date: 11/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-help-viewer
ms.topic: conceptual
f1_keywords:
- hv_general
helpviewer_keywords:
- Microsoft Help Viewer Help
- Help Viewer, printing a topic
- printing a topic [Help Viewer]
- Help Viewer, toolbar
- Help on Help [Help Viewer]
- Help Viewer, window components
- Help Viewer, navigating
- toolbar [Help Viewer]
ms.assetid: 74e41666-2ce8-4ac0-a0e5-3723d1e322c2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: be587e708857a5c46c92986decff75a4807f8897
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="microsoft-help-viewer"></a>Microsoft Help Viewer

您可以使用 Microsoft Help Viewer 在本機電腦上安裝並檢視各種產品和技術的內容，包括 Visual Studio、.NET Framework、語言參考、SQL Server 和 Windows 程式開發。 說明檢視器可讓您：

-   尋找並下載內容集，這也稱為書籍。

-   瀏覽和搜尋目錄，依標題尋找主題。

-   查詢索引中的主旨。

-   使用全文檢索搜尋來尋找資訊。

-   檢視主題、將主題加入書籤以及列印。

若要安裝說明檢視器，請參閱 [Microsoft Help Viewer 安裝](../ide/microsoft-help-viewer-installation.md)。 若要在說明檢視器中開始閱讀說明主題，而不要在線上閱讀，請在 Visual Studio 中移至 [說明] 功能表，然後選擇 [設定說明偏好] > [在說明檢視器中啟動]。

## <a name="help-viewer-tour"></a>說明檢視器導覽

您可以使用瀏覽索引標籤，尋找已安裝內容中的資訊，在主題索引標籤中檢視已安裝的內容，以及使用 [管理內容] 索引標籤來管理內容。也可以使用工具列上的按鈕來執行其他工作，並在視窗右下角中尋找其他資訊。

### <a name="navigation-tabs"></a>瀏覽索引標籤

|索引標籤|描述|
|---|-----------|
|內容|將安裝的內容顯示為階層 (目錄)。 您可以指定條件來篩選顯示的標題。|
|索引|顯示已編製索引的詞彙按字母順序排列的清單。 您可以搜尋索引、指定條件來篩選項目，以及要求索引項目包含指定的文字或以其開頭。|
|我的最愛|您可以選擇 [加到我的最愛] 按鈕將主題設為「我的最愛」，那些主題就會出現在此索引標籤中。[記錄] 區段會顯示您最近檢視過的主題清單。|
|搜尋|提供一個文字方塊，您可以用來搜尋內容中任何位置的詞彙，包括程式碼和主題標題。|

### <a name="view-topics"></a>檢視主題

每個主題都會在它自已的索引標籤中出現，而且您可以同時開啟多個主題。

### <a name="manage-content"></a>管理內容

您可以使用 [管理內容] 索引標籤來安裝、更新、移動和刪除內容。在索引標籤頂端，您可以使用 [安裝來源] 控制項，指定是否要從網路位置或是磁碟或 URI 安裝書籍。 [本機存放區路徑] 方塊會顯示在本機電腦上安裝書籍的位置，您可以選擇 [移動] 按鈕將它們移至不同的位置。

內容清單會顯示哪些書籍可以安裝或已安裝、更新是否可用，以及顯示每本書的大小。 您可以選擇適當的 [新增] 或 [移除] 連結，然後選擇 [暫止的變更] 窗格底下的 [更新] 按鈕，安裝或移除一本或多本書籍。 如果您已安裝的任何書籍之更新可用，您可以在視窗底部選擇 [按一下這裡立即下載] 連結來重新整理該內容。 此外，當您安裝其他書籍時，如果更新可用，就會重新整理所有已安裝的書籍。

> [!NOTE]
> 如果說明檢視器的系統管理員停用這些功能，或是沒有網際網路存取可供使用，則 [管理內容] 索引標籤的功能可能會不同。

### <a name="toolbar-buttons"></a>工具列按鈕

[說明檢視器] 視窗中的工具列包含下列按鈕：

-   [顯示內容中的主題] 按鈕會在 [內容] 索引標籤中顯示主題的位置。

-   [加到我的最愛] 按鈕會將使用中的主題加到 [我的最愛] 索引標籤。

-   [在主題中尋找] 按鈕會反白顯示使用中主題的搜尋文字。

-   [列印] 按鈕會列印或顯示使用中主題的預覽。

-   [檢視器選項] 按鈕會顯示設定，例如出現的文字要有多大、要傳回多少搜尋結果、要在歷程記錄顯示多少主題，以及是否要線上檢查更新。

-   [管理內容] 按鈕讓 [管理內容] 索引標籤成為使用中。

-   右側的小三角形會開啟索引標籤清單，包含主題索引標籤和 [管理內容] 索引標籤。您可以選擇某個索引標籤名稱，使它成為作用中的索引標籤。

## <a name="see-also"></a>另請參閱

- [Microsoft Help Viewer 安裝](../ide/microsoft-help-viewer-installation.md)
- [Help Viewer 系統管理員指南](../ide/help-viewer-administrator-guide.md)
- [安裝與管理本機內容](../ide/install-and-manage-local-content.md)
