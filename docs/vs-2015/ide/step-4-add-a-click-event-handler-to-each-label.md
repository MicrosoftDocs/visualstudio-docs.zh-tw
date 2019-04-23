---
title: 步驟 4：將 Click 事件處理常式新增至每個標籤 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 16bdbc7c-4129-411d-bace-f4a3e5375975
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9f23d0593129cae2732c8b4df14b3f5e2d5a69f7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60051371"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>步驟 4：將 Click 事件處理常式新增至每一個標籤
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

配對遊戲的運作方式如下：  
  
1. 當玩家選擇其中一個含有隱藏圖示的方形時，則程式會將圖示色彩變更為黑色，以便對玩家顯示圖示。  
  
2. 然後，玩家會選擇另一個隱藏的圖示。  
  
3. 如果圖示相符，則會保持可見狀態。 如果不相符，則這兩個圖示會再次隱藏。  
  
   若要讓您的程式以該種方式運作，您可加入 Click 事件處理常式，以變更已選擇標籤的色彩。  
  
### <a name="to-add-a-click-event-handler-to-each-label"></a>若要將 Click 事件處理常式加入至每一個標籤  
  
1. 在 [Windows Form 設計工具] 中開啟表單。 在 [方案總管] 中，選擇 Form1.cs 或 Form1.vb。 在功能表列上，選擇 [檢視]、[設計工具]。  
  
2. 選擇第一個 Label 控制項以選取該項目。 接著，按住 CTRL 鍵，同時選擇其他每一個標籤加以選取。 確定已選取每一個標籤。  
  
3. 在 [屬性] 視窗中選擇工具列上的 [事件] 按鈕，檢視 [屬性] 視窗中的 [事件] 頁面。 向下捲動至 **Click** 事件，並在方塊中輸入 **label_Click**，如下列圖片所示。  
  
     ![顯示 Click 事件的 [屬性] 視窗](../ide/media/express-labelclick.png "Express_labelClick")  
顯示 Click 事件的 [屬性] 視窗  
  
4. 選擇 ENTER 鍵。 IDE 會將名稱為 `label_Click()` 的 Click 事件處理常式加入至程式碼，並將它連結至表單上的每一個標籤。  
  
5. 填入程式碼的其餘部分，如下所示：  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#4](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#4)]
     [!code-vb[VbExpressTutorial4Step2_3_4#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#4)]  
  
    > [!NOTE]
    >  如果您是透過複製並貼上 `label_Click()` 程式碼區塊而非手動輸入程式碼，請務必取代現有的 `label_Click()` 程式碼。 否則，您將會產生重複的程式碼區塊。  
  
    > [!NOTE]
    >  您可能會發現事件處理常式上方的 `object sender` 與[教學課程 2：建立計時的數學測驗](../ide/tutorial-2-create-a-timed-math-quiz.md)教學課程。 由於您會將不同的 Label 控制項 Click 事件連結至單一事件處理常式方法，因此不論使用者選擇哪一個標籤，都會呼叫相同的方法。 此事件處理常式方法需要知道已選擇哪一個標籤，因此它會對該 Label 控制項使用名稱 **sender** 來加以識別。 此方法的第一行告知程式，它不只是一個一般物件，還是一個 Label 控制項，而且它會使用名稱 **clickedLabel** 來存取標籤的屬性和方法。  
  
     這個方法會先檢查是否已成功地將 **clickedLabel** 從物件轉換為 Label 控制項。 如果轉換不成功，則其值為 `null` (C#) 或 `Nothing` (Visual Basic)，而且您不會想執行方法中其餘部分的程式碼。 接下來，此方法會使用 Label 的 **ForeColor** 屬性來檢查已選擇標籤的文字色彩。 如果 Label 的文字色彩為黑色，則表示已選擇該圖示，且方法已執行完成 (這就是 `return` 陳述式的作用：它會告訴程式停止執行此方法)。否則，表示尚未選擇該圖示，因此，程式會將標籤的文字色彩變更為黑色。  
  
6. 在功能表列上選擇 [檔案]、[全部儲存] 以儲存進度，然後在功能表列上選擇 [偵錯]、[開始偵錯] 以執行程式。 您應該會看到一個藍色背景的空白表單。 在該表單中選擇任一個儲存格，應該就可以看見其中一個圖示。 繼續在表單中選擇不同位置。 當您選擇圖示時，圖示應該就會出現。  
  
### <a name="to-continue-or-review"></a>若要繼續或檢視  
  
- 若要前往下一個教學課程步驟，請參閱[步驟 5：加入標籤參考](../ide/step-5-add-label-references.md)。  
  
- 若要回到上一個教學課程步驟，請參閱[步驟 3：將隨機圖示指派給每個標籤](../ide/step-3-assign-a-random-icon-to-each-label.md)。
