---
title: 步驟 2：執行您的圖片檢視器應用程式
ms.date: 09/06/2019
ms.assetid: 9a8fe90e-c97b-4e98-b6c8-0c6b3962c49d
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6c7e90f8113f5fa03da907db5dbb8f374a564e7
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70887927"
---
# <a name="step-2-run-your-picture-viewer-app"></a>步驟 2：執行您的圖片檢視器應用程式

當您建立 Windows Forms 應用程式專案時，實際上會建立一個執行的程式。 在本教學課程中，您的圖片檢視器應用&mdash;程式尚未執行太多動作，雖然它會這麼做。 目前，它會顯示一個空白視窗，顯示標題列中的 [ **Form1** ]。

以下是執行應用程式的方式。 

1. 選擇下列其中一種方法：

    - 選擇 **F5** 鍵。

    - 在功能表列上，依序選擇 [偵錯] > [開始偵錯]。

    - 在工具列上，選擇 [**開始調試**] 按鈕，如下所示：

      ![開始調試工具列按鈕](../ide/media/express_icondebug.png)<br>
      ***開始調試****工具列按鈕*

1. Visual Studio 會執行您的應用程式，而名為**Form1**的視窗隨即出現。 下列螢幕擷取畫面顯示您剛建立的應用程式。 應用程式正在執行，您很快就會新增到其中。

     ![Windows Forms 應用程式正在執行](../ide/media/express_firstrun.png)<br>
***Windows Forms 應用程式*** *，執行*

1. 回到 Visual Studio 的整合式開發環境（IDE），然後查看新的工具列。 當您執行應用程式時，工具列上會出現其他按鈕。 這些按鈕可讓您執行停止和啟動應用程式之類的動作，並協助您追蹤任何可能發生的錯誤（bug）。 在此範例中，我們會使用它來啟動和停止應用程式。

     ![調試工具列](../ide/media/express_debugtoolbar.png)<br>
***調試****工具列*

1. 使用下列其中一種方法來停止您的應用程式：

    - 在工具列上選擇 [停止偵錯] 按鈕。

    - 在功能表列上，依序選擇 [偵錯] > [停止偵錯]。

    - 使用您的鍵盤，然後按**Shift** + **F5**。

    - 選擇 [Form1] 視窗右上角的 **X** 按鈕。

    > [!NOTE]
    > 當您從 IDE 內部執行應用程式時，它稱為「偵錯工具」，因為您通常會這麼做，以便找出並修正應用程式中的 bug （錯誤）。 雖然此應用程式很小，而且實際上不會執行任何動作，但仍是真正的程式。 您遵循相同程序執行和偵錯其他程式。 若要深入了解偵錯，請參閱[偵錯工具簡介](../debugger/debugger-feature-tour.md)。

## <a name="next-steps"></a>後續步驟

* 若要移至下一個教學課程步驟 **，請參閱[步驟3：設定您的窗](../ide/step-3-set-your-form-properties.md)體屬性。**

* 若要回到上一個教學課程步驟，請參閱[步驟 1：建立 Windows Forms 應用程式專案](../ide/step-1-create-a-windows-forms-application-project.md)。

## <a name="see-also"></a>另請參閱

* [教學課程 2：建立計時的數學測驗](tutorial-2-create-a-timed-math-quiz.md)
* [教學課程 3：建立配對遊戲](tutorial-3-create-a-matching-game.md)
