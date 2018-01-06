---
title: "程式碼編輯器中檢視資料提示方塊中的資料值 |Microsoft 文件"
ms.custom: 
ms.date: 07/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "38"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 178bd1768474eaaaf760e2ef4feecfe0e1519bee
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>在資料提示方塊程式碼編輯器中的檢視資料值
資料提示方塊提供方便的方法，讓您在偵錯期間檢視程式中的變數資訊。 資料提示方塊只能夠在中斷模式中運作，並且只能使用目前執行範圍內的變數。
  
### <a name="to-display-a-datatip"></a>若要顯示資料提示方塊  
  
1. 設定中斷點並開始偵錯 (按**F5**)。

2. 在暫停偵錯工具中，將滑鼠指標放在目前範圍中的任何變數。
  
     資料提示方塊就會出現。
  
3.  當您移除滑鼠指標時，資料提示方塊就會消失。 若要固定 DataTip，讓它保持開啟，請按一下**固定在來源**圖示或以滑鼠右鍵按一下變數，然後按一下**固定在來源**。

    ![固定資料提示方塊](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

    > [!NOTE]
    > 資料提示一律在暫停執行的內容中評估，而不是在游標停留的內容中評估。 如果您將游標停留在另一個函式的變數上，而該變數的名稱與目前內容中變數的名稱相同，則將另一個函式中的變數值當做目前內容中的變數值顯示。
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>若要取消固定資料提示方塊並讓它浮動  
  
-   在固定資料提示方塊中，按一下**從來源取消固定**圖示。  
  
     固定圖示會變更為已取消固定的位置。 資料提示方塊現在會浮動在任何開啟視窗的上方。 當偵錯工作階段結束時，浮動的資料提示方塊就會關閉。  
  
### <a name="to-repin-a-floating-datatip"></a>若要重新固定浮動的資料提示方塊  
  
-   按一下資料提示方塊中的固定圖示。  
  
     固定圖示會變更為已固定的位置。 如果資料提示方塊位在來源視窗外部，則會停用固定圖示，而且無法固定資料提示方塊。  
  
### <a name="to-close-a-datatip"></a>若要關閉資料提示方塊  
  
-   將滑鼠指標放在資料提示方塊，然後按一下 **關閉**圖示。  
  
### <a name="to-close-all-datatips"></a>若要關閉所有資料提示方塊  
  
-   在**偵錯**功能表上，按一下 **清除所有 DataTips**。  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>若要關閉特定檔案的所有資料提示方塊  
  
-   在**偵錯**功能表上，按一下 **清除所有 DataTips 釘選到***檔案*。  
  
## <a name="expand-and-edit-information"></a>展開和編輯資訊  
 您可以使用資料提示方塊展開陣列、結構或物件，以便檢視其成員。 也可以從資料提示方塊編輯變數值。  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>若要展開變數以檢視項目  
  
-   在資料提示方塊中，將滑鼠指標放 **+** 前面的變數名稱的符號。  
  
    變數就會展開並以樹狀目錄格式來顯示項目。

    ![檢視資料提示方塊](../debugger/media/dbg-tour-data-tips.gif "檢視資料提示方塊")
  
    當變數展開時，您可以使用鍵盤上的方向鍵上下移動。 或者，您也可以使用滑鼠。  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>若要使用資料提示方塊編輯變數的值  
  
1.  按一下資料提示方塊中的值。 唯讀值會停用這項功能。  
  
2.  輸入新的值，然後按 ENTER 鍵。  
  
## <a name="making-a-datatip-transparent"></a>讓資料提示方塊變成透明  
 如果您想要看到資料提示方塊後方的程式碼，則可以暫時讓資料提示方塊變成透明。 此選項不適用於固定或浮動的 DataTips。  
  
#### <a name="to-make-a-datatip-transparent"></a>若要讓資料提示方塊變成透明  
  
-   在資料提示方塊中，按 CTRL 鍵。  
  
     只要您按住 CTRL 鍵，資料提示方塊就會維持透明。  
  
## <a name="visualize-complex-data-types"></a>以視覺化方式檢視複雜資料型別  
 如果在資料提示方塊、 一個或多個變數名稱旁邊的放大鏡圖示會出現[視覺化檢視](../debugger/create-custom-visualizers-of-data.md)，例如[字串視覺化檢視](../debugger/string-visualizer-dialog-box.md)，可用於該資料類型的變數。 您可以使用視覺化檢視，以更有意義的方式 (通常是圖形) 來顯示資訊。
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>若要使用視覺化檢視來檢視變數的內容  
  
-   按一下放大鏡圖示![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "視覺化檢視圖示")選取預設的資料類型的視覺化檢視。  
  
     -或-  
  
     按一下視覺化檢視旁邊的快顯箭號，以從資料型別的適當視覺化檢視清單中進行選取。  
  
     視覺化檢視會顯示資訊。  
  
## <a name="add-information-to-a-watch-window"></a>將資訊加入至監看式視窗  
 如果您想要繼續監看的變數在清單檢視中，您可以將變數加入**監看式**視窗從資料提示方塊。  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>若要將變數加入至監看式視窗  
  
-   資料提示方塊中，以滑鼠右鍵按一下，然後按一下 **加入監看式**。  
  
     變數會加入至**監看式**視窗。 如果您使用的版本支援多個**監看式**windows 中，變數會加入至**監看式 1。**  
  
## <a name="import-and-export-datatips"></a>匯入和匯出資料提示方塊  
 您可以將資料提示方塊匯出至 XML 檔，之後您就可以將這個檔案與同事共用，或是使用文字編輯器進行編輯。  
  
#### <a name="to-export-datatips"></a>若要匯出資料提示方塊  
  
1.  在 [偵錯] 功能表上按一下**匯出 DataTips**。  
  
     **匯出 DataTips**  對話方塊隨即出現。  
  
2.  若要瀏覽至您要儲存 XML 檔中，輸入中的檔案名稱的位置使用標準檔案技術**檔案名稱**方塊，然後再按一下**確定**。  
  
#### <a name="to-import-datatips"></a>若要匯入資料提示方塊  
  
1.  在 [偵錯] 功能表上按一下**匯入 DataTips**。  
  
     **匯入 DataTips**  對話方塊隨即出現。  
  
2.  使用對話方塊來尋找您想要開啟，然後按一下的 XML 檔案**確定**。  
  
## <a name="see-also"></a>請參閱  
 [在 偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)   
 [監看式和快速監看式視窗](../debugger/watch-and-quickwatch-windows.md)   
 [建立自訂視覺化檢視](../debugger/create-custom-visualizers-of-data.md)   