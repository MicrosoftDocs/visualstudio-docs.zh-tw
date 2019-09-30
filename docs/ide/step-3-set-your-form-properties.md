---
title: 步驟 3：設定表單屬性
ms.date: 08/30/2019
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 870179243f99501cac7aaa68ce9929ae589ba79e
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118957"
---
# <a name="step-3-set-your-form-properties"></a>步驟 3：設定表單屬性

接下來，您要使用 [屬性] 視窗變更表單的外觀。

## <a name="how-to-set-your-form-properties"></a>如何設定您的表單內容

1. 確定您在查看 **Windows Forms 設計工具**。 在 Visual Studio 整合式開發環境 (IDE) 中，選擇 [Form1.cs [設計]] 索引標籤 (或 Visual Basic 中的 [Form1.vb [設計]] 索引標籤)。

1. 選擇表單 [Form1] 內的任何位置來選取它。 查看 [屬性] 視窗，現在應該會顯示表單的屬性。 表單有各種屬性。 例如，您可以設定前景和背景色彩、表單頂端顯示的標題文字、表單的大小和其他屬性。

   > [!NOTE]
   > 如果 [**屬性**] 視窗沒有出現，請選擇工具列上的 [**停止調試**程式] 按鈕，或直接關閉視窗，以停止您的應用程式。 如果應用程式已停止，而您仍然看不到 [**屬性**] 視窗，請在功能表列上選擇 [**視圖** > **屬性視窗]** 。

1. 選取表單之後，在 [屬性] 視窗中尋找 [文字] 屬性。 根據清單排序的方式，您可能需要向下捲動。 選擇 [文字]，鍵入 **Picture Viewer**，然後選擇 **Enter**。  您的表單現在應該會在其標題列中顯示 [文字**圖片檢視器**]，而 [**屬性**] 視窗看起來應該類似下列螢幕擷取畫面。

    ![屬性視窗](../ide/media/express_edittextproperty.png)<br>
   ***屬性****視窗*

   > [!NOTE]
   > 屬性可以依 [分類] 或 [字母順序] 檢視來排序。 您可以使用 [屬性] 視窗上的按鈕，在這兩個檢視之間切換。 在本教學課程中，透過 [字母順序] 檢視比較容易找到屬性。

1. 返回 **Windows Forms 設計工具**。 選擇表單的右下方拖曳控點，即表單右下方的白色小方塊，如下所示。

    ![拖曳控點](../ide/media/express_bottomrt_drag.png)<br>
   *拖曳控點*

    拖曳控點來調整表單大小，使表單變得較寬且稍微高一些。

1. 查看 [屬性] 視窗，並注意 **Size** 屬性已變更。 每當您調整表單的大小時，**Size** 屬性就會變更。 嘗試拖曳表單的控點，將其調整為大約 **550, 350** (不需要很精確) 的表單大小，這樣應該很適合此專案。 或者，您可以直接在 **Size** 屬性中輸入值，然後選擇 **Enter** 鍵。

1. 再次執行您的應用程式。 請記住，您可以使用下列任何方法來執行您的應用程式。

   - 選擇 **F5** 鍵。

   - 在功能表列上，依序選擇 [偵錯] > [開始偵錯]。

   - 在工具列上選擇 [開始偵錯] 按鈕，如下所示。

      ![開始調試工具列按鈕](../ide/media/express_icondebug.png)<br>
     ***開始調試****工具列按鈕*

     就像之前一樣，IDE 會建立並執行您的應用程式，而視窗隨即出現。

1. 在進行下一個步驟之前，請停止您的應用程式，因為 IDE 不會讓您在應用程式執行時加以變更。 請記住，您可以使用下列任何方法來停止您的應用程式。

   - 在工具列上選擇 [停止偵錯] 按鈕。

   - 在功能表列上，依序選擇 [偵錯] > [停止偵錯]。

   - 使用您的鍵盤，然後按**Shift** + **F5**。

   - 選擇 [**圖片檢視器**] 視窗右上角的 [ **X** ] 按鈕。

## <a name="next-steps"></a>後續步驟

* 若要移至下一個教學課程步驟 **，請參閱[步驟4：使用 TableLayoutPanel 控制項](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)** 來配置您的表單。

* 若要回到上一個教學課程步驟，請參閱[步驟 2：執行您的圖片查看](../ide/step-2-run-your-program.md)器應用程式。

## <a name="see-also"></a>另請參閱

* [教學課程 2：建立計時的數學測驗](tutorial-2-create-a-timed-math-quiz.md)
* [教學課程 3：建立配對遊戲](tutorial-3-create-a-matching-game.md)
