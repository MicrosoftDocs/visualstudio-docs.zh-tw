---
title: 步驟 3：將隨機圖示指派給每個標籤
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 293548d1fcb1e06391d052aefa64b19065ba1372
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>步驟 3：將隨機圖示指派給每個標籤
如果讓圖示在每個遊戲的相同儲存格中顯示，這樣就不夠有挑戰性。 若要避免此情形，請使用 `AssignIconsToSquares()` 方法在表單上將圖示隨機指派給 Label 控制項。  

### <a name="to-assign-a-random-icon-to-each-label"></a>若要將隨機圖示指派給每一個標籤  

1.  在加入下列程式碼之前，請考慮方法的運作方式。 有新的關鍵字：在 Visual C# 中為 `foreach`，而在 Visual Basic 中為 `For Each`  (其中一行會被故意標記為註解，而在此程序的結尾處予以說明)。  

     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_1.vb)]  

2.  如上一個步驟所示，加入 `AssignIconsToSquares()` 方法。 您可以將它放在您於[步驟 2：新增隨機物件和圖示清單](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)中新增的程式碼正下方。  

     如先前所述，您的 `AssignIconsToSquares()` 方法中有一些新項目：在 Visual C# 中為 `foreach`，而在 Visual Basic 中為 `For Each`。 您隨時要多次執行相同的動作時，可以使用 `For Each` 迴圈。 在這種情況下，您要對 TableLayoutPanel 上的每一個標籤執行相同的陳述式，如下列程式碼所說明。 第一行建立名稱為 `control` 的變數，會在控制項上執行迴圈中的陳述式時，儲存該控制項 (一次儲存一個控制項)。  

     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_2.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_2.vb)]  

    > [!NOTE]
    >  因為 "iconLabel" 和 "control" 這兩個名稱都屬描述性，所以會加以使用。 您可以使用任何名稱來取代這些名稱，程式碼的作用完全相同 (只要您變更迴圈內每一個陳述式中的名稱即可)。  

     `AssignIconsToSquares()` 方法會反覆通過 TableLayoutPanel 中的每一個 Label 控制項，並為每一個控制項執行相同的陳述式。 這些陳述式會從您在[步驟 2：新增隨機物件和圖示清單](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)中新增的清單提取一個隨機圖示。 (這就是您為何將兩個圖示都包含在清單中的緣故，所以會有一對圖示指派給隨機 Label 控制項)。  

     仔細留意在 `foreach` 或 `For Each` 迴圈內部執行的程式碼。 這個程式碼在此處重現。  

     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_3.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_3.vb)]  

     第一行將 `control` 變數轉換為名為 `iconLabel` 的 Label。 下一行為 `if` 陳述式，會檢查以確定轉換是否成功。 如果轉換成功，則會執行 `if` 陳述式中的陳述式。 (您可以回想一下上一個教學課程中，其中 `if` 陳述式是用來評估您所指定的任何條件)。`if` 陳述式中的第一行會建立名稱為 `randomNumber` 的變數，其中包含亂數，對應到圖示清單中的其中一個項目。 若要這樣做，該行使用您先前建立之 `Next` 物件的 `Random` 方法。 `Next` 方法會傳回亂數。 這一行也使用 `Count` 清單的 `icons` 屬性，決定從中選擇亂數的範圍。 下一行將圖示清單的其中一個項目指定至標籤的 `Text` 屬性。 註解行在本主題稍後加以說明。 最後，`if` 陳述式中的最後一行從清單中移除已加入至表單的圖示。  

     請記住，如果您不確定程式碼某些部分所執行的動作，可以將滑鼠指標放在程式碼項目上並檢閱顯示的工具提示。 使用 Visual Studio 偵錯工具時，您也可以在程式執行時對每一行程式碼進行逐步執行。 如需詳細資訊，請參閱 [How Do I: Step with The Debugger in Visual Studio?](http://msdn.microsoft.com/vstudio/ee672313.aspx) (如何：在 Visual Studio 中逐步執行偵錯工具？) 或[使用偵錯工具巡覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)。  

3.  若要在程式啟動時使用圖示填滿遊戲面板，您必須呼叫 `AssignIconsToSquares()` 方法。 如果您使用的是 Visual C#，請在 `Form1` 建構函式中將陳述式新增至對 `InitializeComponent()` 方法的呼叫正下方，如此您的表單會呼叫新方法，在表單顯示之前自行設定。 當您建立新的物件 (例如類別或結構) 時會呼叫建構函式。 如需詳細資訊，請參閱[建構函式 (C# 程式設計手冊)](http://msdn.microsoft.com/library/ace5hbzh.aspx)，若是在 Visual Basic 中，則請參閱[使用建構函式和解構函式](http://msdn.microsoft.com/library/2z08e49e.aspx)。  

     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_4.cs)]  

     對於 Visual Basic，請將 `AssignIconsToSquares()` 方法呼叫加入至 `Form1_Load` 方法，使程式碼看起來如下。  

    ```vb  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
        AssignIconsToSquares()  
    End Sub  
    ```  

4.  儲存並執行您的程式。 它應該會顯示一個表單，內含已指派給每一個標籤的隨機圖示。  

5.  關閉程式，然後再執行一次。 請注意，不同的圖示會指派給每一個標籤，如下列圖片所示。  

     ![含有隨機圖示的配對遊戲](../ide/media/express_tut4step3.png "Express_Tut4Step3")  
含有隨機圖示的配對遊戲  

     因為您未隱藏它們，所以圖示現在是可見的。 若要讓玩家看不到它們，您可以將每個 Label 的 `Forecolor` 屬性設定為與其 `BackColor` 屬性相同的色彩。  

    > [!TIP]
    >  另一種隱藏控制項 (如 Label) 的方式是將其 **Visible** 屬性設定為 `False`。  

6.  若要隱藏圖示，請停止程式並移除 `For Each` 迴圈內部程式碼註解行的註解標記。  

     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_5.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_5.vb)]  

7.  在功能表列上，選擇 [全部儲存] 按鈕以儲存您的程式，然後執行它。 圖示似乎都已消失，只有一個藍色背景會出現。 不過，會隨機指派圖示，而且都還在那裡。 因為圖示與背景的色彩相同，所以玩家會看不見它。 畢竟，如果玩家可以立即查看所有圖示，這就不是一個非常具有挑戰性的遊戲了！  

### <a name="to-continue-or-review"></a>繼續或檢視  

-   若要移至下一個教學課程步驟，請參閱[步驟 4：將 Click 事件處理常式新增至每個標籤](../ide/step-4-add-a-click-event-handler-to-each-label.md)。  

-   若要返回上一個教學課程步驟，請參閱[步驟 2：新增隨機物件和圖示清單](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)。
