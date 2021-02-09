---
title: 在資料提示中查看變數值 |Microsoft Docs
description: 您可以使用資料提示來輕鬆地查看變數的相關資訊，包括陣列和結構，同時進行調試。 您也可以修改值。
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b5c9d0449fca38371e07ddaca6cef8758f53a2aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904920"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>在程式碼編輯器的資料提示中查看資料值

資料提示方塊提供方便的方法，讓您在偵錯期間檢視程式中的變數資訊。 資料提示方塊只能夠在中斷模式中運作，並且只能使用目前執行範圍內的變數。 如果這是您第一次嘗試進行程式碼的偵錯工具，您可能會想要在進行這篇文章之前，先閱讀絕對初學者和[調試](../debugger/write-better-code-with-visual-studio.md)[程式的偵錯工具](../debugger/debugging-absolute-beginners.md)。

## <a name="work-with-datatips"></a>使用資料提示

資料提示只會出現在中斷模式中，而且只會顯示在目前執行範圍內的變數上。

### <a name="display-a-datatip"></a>顯示資料提示

1. 在您的程式碼中設定中斷點，然後按 **F5** 或選取 [ **Debug**  >  **開始調試** 程式] 開始進行偵錯工具。

1. 在中斷點暫停時，將滑鼠停留在目前範圍中的任何變數上。 資料提示隨即出現，並顯示變數的名稱和目前值。

### <a name="make-a-datatip-transparent"></a>將資料提示變成透明

若要讓資料提示的透明查看其下的程式碼，請在資料提示中按 **Ctrl**。 只要按住 **Ctrl** 鍵，資料提示就會保持透明。 這不適用於釘選或浮動的資料提示。
### <a name="pin-a-datatip"></a>釘選資料提示

若要釘選資料提示，使其保持開啟，請選取圖釘 **釘選至來源** 圖示。

![釘選資料提示](../debugger/media/dbg-tips-data-tips-pinned.png "釘選資料提示")

您可以在程式碼視窗周圍拖曳，以移動釘選的資料提示。 圖釘圖示會出現在資料提示釘選到的線條旁的裝訂邊中。

>[!NOTE]
>資料提示一律會在暫停執行的內容中進行評估，而不是在目前的資料指標或資料提示位置上進行評估。 如果您將滑鼠停留在另一個函式的變數上，而該變數的名稱與目前內容中的變數相同，則會顯示目前內容中的變數值。

### <a name="unpin-a-datatip-from-source"></a>從來源取消釘選資料提示

若要浮上釘選的資料提示，請將滑鼠停留在資料提示上方，並從內容功能表中選取圖釘圖示。

圖釘圖示會變更為取消釘選的位置，而資料提示現在會浮動，或可拖曳至所有開啟的視窗上方。 當調試進程結束時，浮動的資料提示會關閉。

### <a name="repin-a-datatip"></a>Repin 資料提示

若要 repin 浮動的資料提示至來源，請在程式碼編輯器中將滑鼠停留在其上方，然後選取圖釘圖示。 圖釘圖示會變更為已釘選的位置，而資料提示會再一次釘選在程式碼視窗中。

如果資料提示是浮動在非原始程式碼視窗上，則圖釘圖示無法使用，也無法 repinned 資料提示。 若要存取圖釘圖示，請將資料提示拖曳至 [程式碼編輯器] 視窗，或提供程式碼視窗焦點給程式碼編輯器視窗。

### <a name="close-a-datatip"></a>關閉資料提示

若要關閉資料提示，請將滑鼠停留在資料提示上方，然後從操作功能表中選取關閉 (**x**) 圖示。

### <a name="close-all-datatips"></a>關閉所有資料提示

若要關閉所有資料提示，請在 [ **調試** ] 功能表上選取 [ **清除所有資料提示**]。

### <a name="close-all-datatips-for-a-specific-file"></a>關閉特定檔案的所有資料提示

若要關閉特定檔案的所有資料提示，請在 [**調試** 程式] 功能表上選取 [**清除所有 \<Filename> 釘選的資料提示**]。

## <a name="expand-and-edit-information"></a>展開和編輯資訊
您可以使用資料提示方塊展開陣列、結構或物件，以便檢視其成員。 也可以從資料提示方塊編輯變數值。

### <a name="expand-a-variable"></a>展開變數

若要展開資料提示中的物件以查看其元素，請將滑鼠停留在專案名稱前面的展開箭號上方，以樹狀形式顯示元素。 若為釘選的資料提示，請選取 **+** 變數名稱之前的，然後展開樹狀結構。

![展開資料提示](../debugger/media/dbg-tour-data-tips.png "展開資料提示")

您可以使用滑鼠或鍵盤上的方向鍵，在展開的視圖中向上和向下移動。

您也可以將展開的專案釘選到釘選的資料提示，並選取其圖釘圖示。 然後，專案會在樹狀結構折迭之後出現在釘選的資料提示中。

### <a name="edit-the-value-of-a-variable"></a>編輯變數的值

若要在資料提示中編輯變數或元素的值，請選取值、輸入新值，然後按 **enter**。 唯讀值的選項已停用。

::: moniker range=">= vs-2019"

## <a name="pin-properties-in-datatips"></a>在資料提示中釘選屬性

> [!NOTE]
> .NET Core 3.0 或更高版本支援此功能。

您可以使用 [ **可釘選屬性** ] 工具，在資料提示中快速檢查物件的屬性。  若要使用此工具，請將滑鼠停留在屬性上，然後選取出現的釘選圖示，或按一下滑鼠右鍵，然後在產生的內容功能表中選取 [ **釘選成員** ] 選項。  這會將該屬性反升到物件之屬性清單的最上方，而屬性名稱和值會顯示在資料提示的右欄中。  若要取消釘選屬性，請再次選取 [釘選] 圖示，或在內容功能表中選取 [取消釘選 **成員** ] 選項。

![在資料提示中釘選屬性](../debugger/media/basic-pin-datatip.gif "在資料提示中釘選屬性")

在資料提示中查看物件的屬性清單時，您也可以切換屬性名稱，並篩選掉未釘選的屬性。  您可以存取任一選項，方法是以滑鼠右鍵按一下包含屬性的資料列，然後在內容功能表中選取 [ **只顯示已釘** 選的成員或 **隱藏值中** 的已釘選成員名稱] 選項。

::: moniker-end

## <a name="visualize-complex-data-types"></a>將複雜的資料類型視覺化

在資料提示方塊中，變數或元素旁的放大鏡圖示表示有一或多個 [視覺化檢視](../debugger/create-custom-visualizers-of-data.md)（例如 [文字視覺化檢視](../debugger/string-visualizer-dialog-box.md)）可供變數使用。 視覺化檢視會以更有意義的方式（有時是圖形化）來顯示資訊。

若要使用資料類型的預設視覺化檢視來查看元素，請選取放大鏡圖示 ![視覺化圖示](../debugger/media/dbg-tips-visualizer-icon.png "視覺化檢視圖示")。 選取放大鏡圖示旁邊的箭號，即可從資料類型的視覺化清單中選取。

## <a name="add-a-variable-to-a-watch-window"></a>將變數新增至監看式視窗

如果您想要繼續監看變數，您可以從資料提示將它新增至 **監看** 式視窗。 以滑鼠右鍵按一下資料提示中的變數，然後選取 [ **新增監看式]**。

變數會出現在 [ **監看** 式] 視窗中。 如果您的 Visual Studio 版本支援多個 **監看** 式視窗，則變數會出現在 **[監看式 1**] 中。

## <a name="import-and-export-datatips"></a>匯入和匯出資料提示

您可以將資料提示匯出至 XML 檔案，您可以使用文字編輯器來共用或編輯該檔案。 您也可以匯入已接收或編輯的資料提示 XML 檔案。

**匯出 DataTips：**

1. 選取 [ **Debug**]  >  **匯出資料提示**。

1. 在 [ **匯出資料** 類型] 對話方塊中，流覽至要儲存 XML 檔案的位置，輸入檔案名，然後選取 [ **儲存**]。

**匯入 DataTips：**

1. 選取 [ **Debug**  >  **Import 資料提示**]。

1. 在 [匯 **入資料提示** ] 對話方塊中，選取您要開啟的資料提示 XML 檔案，然後選取 [ **開啟**]。

## <a name="see-also"></a>另請參閱
- [什麼是偵錯？](../debugger/what-is-debugging.md)
- [偵錯技術和工具](../debugger/write-better-code-with-visual-studio.md)
- [先查看調試](../debugger/debugger-feature-tour.md)
- [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)
- [監看式及快速監看式視窗](../debugger/watch-and-quickwatch-windows.md)
- [建立自訂視覺化檢視](../debugger/create-custom-visualizers-of-data.md)
