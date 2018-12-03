---
title: 檢視 DataTips 中的資料值，在程式碼編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 11/21/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c473faf449176b38d4505675b1060618344db0d6
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388156"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>在資料提示方塊中，程式碼編輯器中的檢視資料值

資料提示方塊是在您的應用程式中檢視變數的相關資訊，在偵錯期間的便利方式。 

如果這是您第一次，偵錯時，您可能想要閱讀[撰寫出更好C#使用 Visual Studio 程式碼](../debugger/write-better-code-with-visual-studio.md)並[偵錯適用於徹底初學者](../debugger/debugging-absolute-beginners.md)閱讀這篇文章之前。
  
## <a name="work-with-datatips"></a>使用資料提示方塊

只有在中斷模式中，而且只在目前執行的範圍中的變數，則會顯示資料提示方塊。

### <a name="display-a-datatip"></a>顯示資料提示方塊  
  
1. 您的程式碼中設定中斷點，並開始偵錯藉由按下**F5**或選取**偵錯** > **開始偵錯**。
  
1. 當在中斷點暫停時暫留在目前的範圍中的任何變數。 資料提示方塊隨即出現，顯示名稱和變數的目前值。

### <a name="make-a-datatip-transparent"></a>讓資料提示方塊變成透明  

若要讓資料提示方塊變成透明，以查看它在資料提示方塊中的程式碼，請按**Ctrl**。 只要您按住資料提示方塊就會保持透明**Ctrl**索引鍵。 這不適用於固定或浮動的 DataTips。  
### <a name="pin-a-datatip"></a>釘選資料提示方塊

若要釘選資料提示方塊，以便它都會維持開啟，請選取 圖釘**釘選到來源**圖示。 

![釘選 DataTip](../debugger/media/dbg-tips-data-tips-pinned.png "釘選資料提示方塊")

您可以藉由拖曳程式碼視窗周圍移動固定資料提示方塊。 圖釘圖示會出現在資料提示方塊已釘選到行旁邊的裝訂邊。 

>[!NOTE]
>在內容中執行暫止、 目前的資料指標或資料提示方塊位置不使用資料提示方塊都會進行評估。 如果您停留在另一個同名的變數在目前內容中的函式中的變數時，會顯示目前內容中變數的值。
  
### <a name="unpin-a-datatip-from-source"></a>取消釘選來源資料提示方塊

Float 固定資料提示方塊，將滑鼠停在資料提示方塊，並從操作功能表中選取圖釘圖示。 

圖釘圖示會變更為已取消釘選的位置，以及資料提示方塊現在會浮動，或可以拖曳上述所有開啟的視窗。 偵錯工作階段結束時，就會關閉浮動的 DataTips。  
  
### <a name="repin-a-datatip"></a>重新固定資料提示方塊  
  
若要重新固定浮動的資料提示方塊至來源，滑鼠停留在程式碼編輯器，並選取圖釘圖示。 圖釘圖示會變更為固定的位置，以及資料提示方塊再次釘選，才能在程式碼視窗。 

如果資料提示方塊透過非原始程式碼視窗浮動窗格，圖釘圖示無法使用，而且 DataTip 無法重新釘選。 若要存取的圖釘圖示，回到資料提示方塊的程式碼編輯器 視窗拖曳它，或讓程式碼視窗焦點。 
  
### <a name="close-a-datatip"></a>關閉資料提示方塊  
  
若要關閉資料提示方塊中，暫留在資料提示方塊，然後選取關閉 (**x**) 從內容功能表中的圖示。  
  
### <a name="close-all-datatips"></a>關閉所有資料提示方塊  
  
若要在關閉所有資料提示方塊中，**偵錯**功能表上，選取**清除所有 DataTips**。  
  
### <a name="close-all-datatips-for-a-specific-file"></a>關閉特定檔案的所有資料提示方塊  
  
若要在關閉特定的檔案，所有資料提示方塊**偵錯**功能表上，選取**清除所有 DataTips 釘選到\<檔名 >**。  
  
## <a name="expand-and-edit-information"></a>展開並編輯資訊  
您可以使用資料提示方塊展開陣列、結構或物件，以便檢視其成員。 也可以從資料提示方塊編輯變數值。  
  
### <a name="expand-a-variable"></a>展開變數

若要展開以查看其項目資料提示方塊中的物件，將滑鼠停留項目名稱，以樹狀結構形式來顯示項目之前的展開箭號。 針對固定資料提示方塊中，選取**+** 之前變數名稱，然後展開 樹狀結構。 

![展開 資料提示方塊](../debugger/media/dbg-tour-data-tips.png "依序展開 資料提示方塊")

您可以在鍵盤上使用滑鼠或方向鍵，若要展開之檢視中向上和向下移動。 

您也可以固定到固定資料提示方塊展開的項目上方暫留然後選取其圖釘圖示。 會出現之後摺疊樹狀目錄中，在固定資料提示方塊上項目。 

### <a name="edit-the-value-of-a-variable"></a>編輯變數的值

若要編輯的變數或資料提示方塊中的項目值，選取值、 輸入新的值，然後按**Enter**。 選取項目已停用唯讀值。  

## <a name="visualize-complex-data-types"></a>視覺化複雜資料類型  

變數或資料提示方塊中的項目旁邊的放大鏡圖示表示該一或多個[視覺化檢視](../debugger/create-custom-visualizers-of-data.md)，例如[文字視覺化檢視](../debugger/string-visualizer-dialog-box.md)，可供使用的變數。 視覺化檢視會以更有意義、 有時圖形化方式顯示資訊。
  
若要檢視的資料類型使用預設視覺化檢視的項目，請選取放大鏡圖示![視覺化檢視圖示](../debugger/media/dbg-tips-visualizer-icon.png "視覺化檢視圖示")。 選取 從資料類型的視覺化檢視的清單中選取放大鏡圖示旁邊的箭號。  

## <a name="add-a-variable-to-a-watch-window"></a>將變數加入監看式視窗  

如果您想要繼續監看變數，您可以將它加入**監看式**視窗從資料提示方塊。 以滑鼠右鍵按一下資料提示方塊中的變數，然後選取**新增監看式**。 

變數會出現在**監看式**視窗。 如果您的 Visual Studio 版本支援多個**監看式** 視窗中，變數會出現在**監看式 1**。 
  
## <a name="import-and-export-datatips"></a>匯入和匯出資料提示方塊  

您可以將資料提示方塊匯出至 XML 檔案，您可以共用，或使用文字編輯器編輯。 您也可以匯入已接收或編輯的資料提示方塊 XML 檔案。 
  
**匯出 DataTips：** 
  
1. 選取 **偵錯** > **匯出 DataTips**。  
   
1. 在 **匯出 DataTips**  對話方塊中，瀏覽至要儲存 XML 檔案中，輸入 檔案名稱的位置，然後按**儲存**。  
  
**匯入 DataTips：** 
  
1. 選取 **偵錯** > **匯入 DataTips**。  
   
1. 在 **匯入 DataTips**對話方塊方塊中，選取您想要開啟此項目，然後選取 資料提示方塊 XML 檔案**開啟**。  

## <a name="see-also"></a>另請參閱  
 [什麼是偵錯？](../debugger/what-is-debugging.md)  
 [撰寫更好C#使用 Visual Studio 程式碼](../debugger/write-better-code-with-visual-studio.md)  
 [率先一睹偵錯](../debugger/debugger-feature-tour.md)   
 [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)   
 [監看式及快速監看式視窗](../debugger/watch-and-quickwatch-windows.md)   
 [建立自訂視覺化檢視](../debugger/create-custom-visualizers-of-data.md)   
