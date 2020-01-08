---
title: 在資料提示中查看變數值 |Microsoft Docs
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf5eda8205dbe0629d0b2801473de83c2f91257e
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404272"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>在程式碼編輯器中查看資料提示中的資料值

資料提示方塊提供方便的方法，讓您在偵錯期間檢視程式中的變數資訊。 資料提示方塊只能夠在中斷模式中運作，並且只能使用目前執行範圍內的變數。 如果這是您第一次嘗試偵錯工具代碼，您可能會想要在進行本文之前，先閱讀適用于徹底初學者和[偵錯工具技術和工具](../debugger/write-better-code-with-visual-studio.md) [的偵錯工具](../debugger/debugging-absolute-beginners.md)。

## <a name="work-with-datatips"></a>使用資料提示

資料提示只會顯示在中斷模式中，而且只會出現在目前執行範圍中的變數上。

### <a name="display-a-datatip"></a>顯示資料提示

1. 在您的程式碼中設定中斷點，然後按**F5**或選取 [ **Debug** ] > [**開始調試**程式] 來啟動偵錯工具。

1. 在中斷點暫停時，將滑鼠停留在目前範圍中的任何變數上。 此時會出現資料提示，顯示變數的名稱和目前的值。

### <a name="make-a-datatip-transparent"></a>將資料提示設為透明

若要讓資料提示透明查看其底下的程式碼，請在資料提示中按**Ctrl**。 只要按住**Ctrl**鍵，資料提示就會保持透明。 這不適用於固定或浮動的資料提示。
### <a name="pin-a-datatip"></a>釘選資料提示

若要釘選資料提示，使其保持開啟狀態，請選取 [圖釘**釘選至來源**] 圖示。

![釘選資料提示](../debugger/media/dbg-tips-data-tips-pinned.png "釘選資料提示")

您可以在程式碼視窗周圍拖曳釘選的資料提示。 圖釘圖示會出現在資料提示所釘選行旁邊的裝訂邊中。

>[!NOTE]
>資料提示一律會在暫止執行的內容中進行評估，而不是在目前的游標或資料提示位置進行評估。 如果您將滑鼠停留在另一個函式中的變數，而該函式的名稱與目前內容中的變數相同，則會顯示目前內容中的變數值。

### <a name="unpin-a-datatip-from-source"></a>從來源取消釘選資料提示

若要浮動釘選的資料提示，請將滑鼠停留在資料提示上，然後從內容功能表中選取圖釘圖示。

圖釘圖示會變更為取消釘選的位置，而資料提示現在會浮動或拖曳至所有開啟的視窗上方。 當調試會話結束時，浮動的資料提示關閉。

### <a name="repin-a-datatip"></a>重新釘選資料提示

若要將浮動的資料提示重新釘選至來源，請將滑鼠停留在程式碼編輯器中，然後選取圖釘圖示。 圖釘圖示會變更為釘選的位置，而資料提示則會再次固定在程式碼視窗中。

如果資料提示方塊浮動于非原始程式碼視窗，則圖釘圖示無法使用，而且資料提示無法 repinned。 若要存取圖釘圖示，請將資料提示拖放到程式碼編輯器視窗中，方法是拖曳它或提供程式碼視窗的焦點。

### <a name="close-a-datatip"></a>關閉資料提示

若要關閉資料提示，請將滑鼠停留在資料提示上方，然後從內容功能表中選取 [關閉] （**x**）圖示。

### <a name="close-all-datatips"></a>關閉所有資料提示

若要關閉所有資料提示，請在 [**調試**] 功能表上，選取 [**清除所有資料提示**]。

### <a name="close-all-datatips-for-a-specific-file"></a>關閉特定檔案的所有資料提示

若要關閉特定檔案的所有資料提示，請在 [**調試**程式] 功能表上，選取 [**清除所有釘選的資料提示]，以 \<Filename >** 。

## <a name="expand-and-edit-information"></a>展開和編輯資訊
您可以使用資料提示方塊展開陣列、結構或物件，以便檢視其成員。 也可以從資料提示方塊編輯變數值。

### <a name="expand-a-variable"></a>展開變數

若要展開資料提示方塊中的物件以查看其元素，請將滑鼠停留在專案名稱前面的展開箭號，以在樹狀結構中顯示元素。 針對釘選的資料提示，請選取變數名稱前面的 **+** ，然後展開樹狀結構。

![展開資料提示](../debugger/media/dbg-tour-data-tips.png "展開資料提示")

您可以使用滑鼠或鍵盤上的方向鍵，在展開的視圖中向上或向下移動。

您也可以將展開的專案移至釘選的資料提示上方，方法是將滑鼠停留在其上方並選取圖釘圖示。 之後，這些專案就會出現在釘選的資料提示方塊中，然後在折迭樹狀結構

### <a name="edit-the-value-of-a-variable"></a>編輯變數的值

若要在資料提示中編輯變數或元素的值，請選取值，輸入新值，然後按**enter**。 唯讀值的選取專案已停用。

::: moniker range=">= vs-2019"

## <a name="pin-properties-in-datatips"></a>在資料提示中釘選屬性

> [!NOTE]
> .NET Core 3.0 或更高版本支援這項功能。

您可以使用 [**可固定屬性**] 工具，在資料提示中快速檢查物件的屬性。  若要使用此工具，請將滑鼠停留在屬性上，然後選取顯示的釘選圖示，或按一下滑鼠右鍵，然後在產生的內容功能表中選取 [**釘選成員為我的最愛**] 選項  這會將該屬性反升至物件之屬性清單的頂端，而屬性名稱和值會顯示在資料提示的右欄中。  若要取消固定屬性，請再次選取釘選圖示，或選取內容功能表中的 [**取消固定成員為我的最愛**] 選項。

![在資料提示方塊中釘選屬性](../debugger/media/basic-pin-datatip.gif "在資料提示方塊中釘選屬性")

在資料提示中查看物件的屬性清單時，您也可以切換屬性名稱，並篩選出未釘選的屬性。  您可以存取任一選項，方法是以滑鼠右鍵按一下包含屬性的資料列，然後在操作功能表中選取 [**只顯示已釘**選的成員] 或 [**隱藏值中的成員名稱**] 選項。

::: moniker-end

## <a name="visualize-complex-data-types"></a>將複雜資料類型視覺化

資料提示方塊中變數或元素旁的放大鏡圖示表示有一或多個[視覺化檢視](../debugger/create-custom-visualizers-of-data.md)（例如[文字視覺化檢視](../debugger/string-visualizer-dialog-box.md)）可供變數使用。 視覺化檢視會以更有意義的方式顯示資訊，有時也是圖形化。

若要使用資料類型的預設視覺化程式來查看元素，請選取放大鏡圖示![視覺化檢視圖示](../debugger/media/dbg-tips-visualizer-icon.png "視覺化檢視圖示")。 選取放大鏡圖示旁的箭號，即可從資料類型的視覺化程式清單中選取。

## <a name="add-a-variable-to-a-watch-window"></a>將變數新增至監看式視窗

如果您想要繼續監看變數，您可以從資料提示方塊將它加入至**監看**式視窗。 以滑鼠右鍵按一下資料提示方塊中的變數，然後選取 [**新增監看式]** 。

變數會出現在 [**監看**式] 視窗中。 如果您的 Visual Studio 版本支援一個以上的**監看**式視窗，則變數會出現在**Watch 1**中。

## <a name="import-and-export-datatips"></a>匯入和匯出資料提示

您可以將資料提示匯出至 XML 檔案，您可以使用文字編輯器來共用或編輯該檔案。 您也可以匯入您已接收或編輯的資料提示 XML 檔案。

**匯出 DataTips：**

1. 選取 [ **Debug** > **匯出資料提示**]。

1. 在 [**匯出資料提示**] 對話方塊中，流覽至要儲存 XML 檔案的位置，輸入檔案名，然後選取 [**儲存**]。

**匯入 DataTips：**

1. 選取 [ **Debug** > 匯**入資料提示**]。

1. 在 [匯**入資料提示**] 對話方塊中，選取您要開啟的資料提示 XML 檔案，然後選取 [**開啟**]。

## <a name="see-also"></a>請參閱
- [什麼是偵錯？](../debugger/what-is-debugging.md)
- [偵錯技術和工具](../debugger/write-better-code-with-visual-studio.md)
- [第一次查看調試](../debugger/debugger-feature-tour.md)
- [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)
- [監看式及快速監看式視窗](../debugger/watch-and-quickwatch-windows.md)
- [建立自訂視覺化檢視](../debugger/create-custom-visualizers-of-data.md)
