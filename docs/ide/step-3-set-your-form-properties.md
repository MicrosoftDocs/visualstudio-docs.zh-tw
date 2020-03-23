---
title: 步驟 3：設定您的表單屬性
ms.date: 08/30/2019
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82dbef4baee72be8ff96f83e436b2587e9a020ea
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579863"
---
# <a name="step-3-set-your-form-properties"></a>步驟 3：設定您的表單屬性

接下來，您要使用 [屬性]**** 視窗變更表單的外觀。

## <a name="how-to-set-your-form-properties"></a>如何設置表單內容

1. 確定您在查看 **Windows Forms 設計工具**。 在 Visual Studio 整合式開發環境 (IDE) 中，選擇 [Form1.cs [設計]]**** 索引標籤 (或 Visual Basic 中的 [Form1.vb [設計]]**** 索引標籤)。

1. 選擇表單 [Form1]**** 內的任何位置來選取它。 查看 [屬性]**** 視窗，現在應該會顯示表單的屬性。 表單有各種屬性。 例如，您可以設定前景和背景色彩、表單頂端顯示的標題文字、表單的大小和其他屬性。

   > [!NOTE]
   > 如果未顯示 **"屬性"** 視窗，請通過選擇工具列上的方形 **"停止調試"** 按鈕停止應用，或者只是關閉視窗。 如果應用已停止，但仍看不到"**屬性"** 視窗，則在功能表列上選擇 **"查看** > **屬性"視窗**。

1. 選取表單之後，在 [屬性]**** 視窗中尋找 [文字]**** 屬性。 根據清單排序的方式，您可能需要向下捲動。 選擇**文本**，鍵入**圖片檢視器**，然後選擇**Enter**。  您的表單現在應在其標題列中包含文本**圖片檢視器**，並且 **"屬性"** 視窗應類似于以下螢幕截圖。

    ![屬性視窗](../ide/media/express_edittextproperty.png)<br>
   ***屬性****視窗*

   > [!NOTE]
   > 屬性可以依 [分類]**** 或 [字母順序]**** 檢視來排序。 您可以使用 [屬性]**** 視窗上的按鈕，在這兩個檢視之間切換。 在本教學課程中，透過 [字母順序]**** 檢視比較容易找到屬性。

1. 返回 **Windows Forms 設計工具**。 選擇表單的右下方拖曳控點，即表單右下方的白色小方塊，如下所示。

    ![拖動手柄](../ide/media/express_bottomrt_drag.png)<br>
   *拖動手柄*

    拖曳控點來調整表單大小，使表單變得較寬且稍微高一些。

1. 查看 [屬性]**** 視窗，並注意 **Size** 屬性已變更。 每當您調整表單的大小時，**Size** 屬性就會變更。 嘗試拖曳表單的控點，將其調整為大約 **550, 350** (不需要很精確) 的表單大小，這樣應該很適合此專案。 作為替代方法，可以直接在**Size**屬性中輸入值，然後選擇**Enter**鍵。

1. 再次運行應用。 請記住，您可以使用以下任何方法運行應用。

   - 選擇 **F5** 鍵。

   - 在功能表列上，選擇**調試** > **開始調試**。

   - 在工具列上選擇 [開始偵錯]**** 按鈕，如下所示。

      ![[開始偵錯] 工具列按鈕](../ide/media/express_icondebug.png)<br>
     ***開始調試****工具列按鈕*

     與之前一樣，IDE 生成並運行你的應用，並顯示一個視窗。

1. 在開始下一步之前，請停止應用，因為 IDE 不會允許您在應用運行時更改應用。 請記住，您可以使用以下任何方法停止應用。

   - 在工具列上選擇 [停止偵錯]**** 按鈕。

   - 在功能表列上，選擇**調試** > **停止調試**。

   - 使用鍵盤，然後按**Shift**+**F5**。

   - 選擇 **"圖片檢視器"** 視窗右上角的**X**按鈕。

## <a name="next-steps"></a>後續步驟

* 要轉到下一個教程步驟，請參閱**[步驟 4：使用表佈局面板控制項佈局表單](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)**。

* 要返回到前面的教程步驟，請參閱步驟[2：運行圖片檢視器應用](../ide/step-2-run-your-program.md)。

## <a name="see-also"></a>另請參閱

* [教程 2：創建有時算數學測驗](tutorial-2-create-a-timed-math-quiz.md)
* [教程 3：創建匹配的遊戲](tutorial-3-create-a-matching-game.md)
