---
title: 使用 Visual Studio 說明檢視器目錄
ms.date: 11/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-help-viewer
ms.topic: conceptual
f1_keywords:
- hv_contents
helpviewer_keywords:
- Help Viewer, table of contents filtering
- Help Viewer, Contents tab
- Contents tab [Help Viewer]
- table of contents filtering [Help Viewer]
ms.assetid: 8b98464d-2b05-4710-ad68-5647e78c6b7b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e7d9ae19cb2a37c6fbf6595a7f3a39895d22190
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-find-topics-in-the-table-of-contents"></a>如何：在目錄中尋找主題

在 [內容] 索引標籤上，您可以使用目錄 (TOC) 來尋找資訊。 目錄是一個可展開的清單，其中包含已安裝書籍中的所有主題。 如需有關目錄巡覽方法的協助工具資訊，請參閱[快速鍵 (說明檢視器)](../ide/shortcut-keys-help-viewer.md)。

> [!IMPORTANT]
> 目錄中可用的主題範圍取決於您選取的篩選條件。

## <a name="filter-the-toc"></a>篩選目錄

您可以篩選目錄來縮小會出現在 [內容] 索引標籤中的主題範圍。只有當標題包含指定詞彙的根時，才會出現在清單中。 例如，如果您指定「疑難排解」做為篩選條件，則只會出現包含「進行疑難排解」或「疑難排解」的標題。 標題不包含該詞彙的節點會以省略符號 (**...**) 摺疊成單一節點。

1.  請選擇 [內容] 索引標籤。

2.  在 [篩選內容] 文字方塊中輸入詞彙。

> [!NOTE]
> 如果執行篩選條件要花很長的時間，則您可使用 `title:` 進階搜尋運算子來快速顯示結果。

## <a name="synchronize-a-topic-with-the-toc"></a>與目錄同步處理主題

如果您已使用索引或全文檢索搜尋功能來開啟主題，則可與主題視窗同步處理目錄，判斷本主題在目錄中的位置。

1.  檢視主題。

2.  按一下工具列上的 [顯示內容中的主題] 按鈕，或按下 **Ctrl**+**S**。

     [內容] 索引標籤隨即開啟，並在目錄中顯示主題的位置。

## <a name="see-also"></a>另請參閱

- [如何：在索引中尋找主題](../ide/how-to-find-topics-in-the-index.md)
- [如何：搜尋主題](../ide/how-to-search-for-topics.md)
- [Microsoft Help Viewer](../ide/microsoft-help-viewer.md)