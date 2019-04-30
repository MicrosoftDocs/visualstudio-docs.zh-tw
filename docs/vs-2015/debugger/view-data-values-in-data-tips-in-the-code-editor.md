---
title: 程式碼編輯器中檢視資料提示中的資料值 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 689d01c7e22cca430693a85e6dedcc7706fda41d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437693"
---
# <a name="view-data-values-in-data-tips--in-the-code-editor"></a>在程式碼編輯器的資料提示中檢視資料值
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

資料提示方塊提供方便的方法，讓您在偵錯期間檢視程式中的變數資訊。 資料提示方塊只能夠在中斷模式中運作，並且只能使用目前執行範圍內的變數。  
  
 在  [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]，DataTips 可以固定至原始程式檔，在特定位置，或它們可以漂浮在所有[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]windows。  
  
### <a name="to-display-a-datatip-in-break-mode-only"></a>若要顯示資料提示方塊 (僅限在中斷模式中)  
  
1. 在來源視窗中，將滑鼠指標放在目前範圍中的任何變數。  
  
    資料提示方塊就會出現。  
  
   > [!NOTE]
   > 資料提示一律在暫停執行的內容中評估，而不是在游標停留的內容中評估。 如果您將游標停留在另一個函式的變數上，而該變數的名稱與目前內容中變數的名稱相同，則將另一個函式中的變數值當做目前內容中的變數值顯示。  
  
2. 當您移除滑鼠指標時，資料提示方塊就會消失。 若要固定 DataTip，使它保持開啟，按一下**釘選到來源**圖示，或  
  
   - 以滑鼠右鍵按一下變數，然後按一下 **釘選到來源**。  
  
     當偵錯工作階段結束時，固定的資料提示方塊就會關閉。  
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>若要取消固定資料提示方塊並讓它浮動  
  
- 在固定資料提示方塊中，按一下**從來源取消固定**圖示。  
  
     固定圖示會變更為已取消固定的位置。 資料提示方塊現在會浮動在任何開啟視窗的上方。 當偵錯工作階段結束時，浮動的資料提示方塊就會關閉。  
  
### <a name="to-repin-a-floating-datatip"></a>若要重新固定浮動的資料提示方塊  
  
- 按一下資料提示方塊中的固定圖示。  
  
     固定圖示會變更為已固定的位置。 如果資料提示方塊位在來源視窗外部，則會停用固定圖示，而且無法固定資料提示方塊。  
  
### <a name="to-close-a-datatip"></a>若要關閉資料提示方塊  
  
- 將滑鼠指標放在資料提示方塊，然後按一下**關閉**圖示。  
  
### <a name="to-close-all-datatips"></a>若要關閉所有資料提示方塊  
  
- 在 **偵錯**功能表上，按一下**清除所有 DataTips**。  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>若要關閉特定檔案的所有資料提示方塊  
  
- 在 **偵錯**功能表上，按一下**清除所有 DataTips 釘選到***檔案*。  
  
## <a name="expanding-and-editing-information"></a>展開和編輯資訊  
 您可以使用資料提示方塊展開陣列、結構或物件，以便檢視其成員。 也可以從資料提示方塊編輯變數值。  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>若要展開變數以檢視項目  
  
- 在資料提示方塊中，將滑鼠指標放**+** 前面的變數名稱的符號。  
  
     變數就會展開並以樹狀目錄格式來顯示項目。  
  
     當變數展開時，您可以使用鍵盤上的方向鍵上下移動。 或者，您也可以使用滑鼠。  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>若要使用資料提示方塊編輯變數的值  
  
1. 按一下資料提示方塊中的值。 唯讀值會停用這項功能。  
  
2. 輸入新的值，然後按 ENTER 鍵。  
  
## <a name="making-a-datatip-transparent"></a>讓資料提示方塊變成透明  
 如果您想要看到資料提示方塊後方的程式碼，則可以暫時讓資料提示方塊變成透明。 此選項不適用於固定或浮動的 DataTips。  
  
#### <a name="to-make-a-datatip-transparent"></a>若要讓資料提示方塊變成透明  
  
- 在資料提示方塊中，按 CTRL 鍵。  
  
     只要您按住 CTRL 鍵，資料提示方塊就會維持透明。  
  
## <a name="visualizing-complex-data-types"></a>視覺化處理複雜資料型別  
 如果在資料提示方塊、 一個或多個變數名稱旁邊的放大鏡圖示會出現[建立自訂視覺化檢視](../debugger/create-custom-visualizers-of-data.md)適用於該資料類型的變數。 您可以使用視覺化檢視，以更有意義的方式 (通常是圖形) 來顯示資訊。  
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>若要使用視覺化檢視來檢視變數的內容  
  
- 按一下放大鏡圖示，以選取資料型別的預設視覺化檢視。  
  
     -或-  
  
     按一下視覺化檢視旁邊的快顯箭號，以從資料型別的適當視覺化檢視清單中進行選取。  
  
     視覺化檢視會顯示資訊。  
  
## <a name="adding-information-to-a-watch-window"></a>將資訊加入至監看式視窗  
 如果您想要繼續監看變數，您可以新增到變數**監看式**視窗從資料提示方塊。  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>若要將變數加入至監看式視窗  
  
- 以滑鼠右鍵按一下資料提示方塊，然後按一下**新增監看式**。  
  
     變數會加入至**監看式**視窗。 如果您使用的版本支援多個**監看式**windows 中，變數會加入至**監看式 1。**  
  
## <a name="importing-and-exporting-datatips"></a>匯入和匯出資料提示方塊  
 您可以將資料提示方塊匯出至 XML 檔，之後您就可以將這個檔案與同事共用，或是使用文字編輯器進行編輯。  
  
#### <a name="to-export-datatips"></a>若要匯出資料提示方塊  
  
1. 在偵錯 功能表中，按一下**匯出 DataTips**。  
  
     **匯出 DataTips**  對話方塊隨即出現。  
  
2. 使用標準檔案技術來瀏覽至您要儲存 XML 檔案中，輸入檔案名稱的位置**檔名**方塊，然後再按一下**確定**。  
  
#### <a name="to-import-datatips"></a>若要匯入資料提示方塊  
  
1. 在偵錯 功能表中，按一下**匯入 DataTips**。  
  
     **匯入 DataTips**  對話方塊隨即出現。  
  
2. 使用對話方塊來尋找您想要開啟，然後按一下 XML 檔案**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)   
 [如何：使用 快速監看式對話方塊](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [建立自訂視覺化檢視](../debugger/create-custom-visualizers-of-data.md)   
 [如何：變更 Windows 偵錯工具的數字格式](http://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)
