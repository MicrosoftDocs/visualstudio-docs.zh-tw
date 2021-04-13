---
title: 步驟2：執行您的圖片檢視器應用程式
description: 瞭解如何執行您的圖片檢視器應用程式。
ms.custom: SEO-VS-2020
ms.date: 09/06/2019
ms.assetid: 9a8fe90e-c97b-4e98-b6c8-0c6b3962c49d
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7113c308416a5ddcd9bf2bb989cf17d31c4fffa6
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296490"
---
# <a name="step-2-run-your-picture-viewer-app"></a>步驟2：執行您的圖片檢視器應用程式

當您建立 Windows Forms 應用程式專案時，實際上會建立執行的程式。 在本教學課程中，您的圖片檢視器應用程式雖然不會有太多的功能 &mdash; 。 現在，它會顯示在標題列中顯示 **Form1** 的空白視窗。

以下是執行應用程式的方式。 

1. 請選擇下列其中一個方法：

    - 選擇 **F5** 鍵。

    - 在功能表列上，選擇 [ **Debug**  >  **開始調試**]。

    - 在工具列上，選擇 [ **開始調試** ] 按鈕，如下所示：

      ![[開始偵錯] 工具列按鈕](../ide/media/express_icondebug.png)<br>
      ***開始調試** _toolbar 按鈕 *

1. Visual Studio 會執行您的應用程式，而且會出現名為 **Form1** 的視窗。 下列螢幕擷取畫面顯示您剛剛建立的應用程式。 應用程式正在執行中，您很快就會新增至該應用程式。

     ![正在執行 Windows Forms 應用程式](../ide/media/express_firstrun.png)<br>
***Windows Forms App** _，_running *

1. 返回至 Visual Studio 整合式開發環境 (IDE) ，然後查看新的工具列。 當您執行應用程式時，工具列上會出現其他按鈕。 這些按鈕可讓您進行一些動作，例如停止和啟動您的應用程式，並協助您追蹤任何錯誤 (錯誤) 它可能有的錯誤。 在此範例中，我們使用它來啟動和停止應用程式。

     ![調試工具列](../ide/media/express_debugtoolbar.png)<br>
***調試** _ _toolbar *

1. 使用下列其中一種方法來停止您的應用程式：

    - 在工具列上選擇 [停止偵錯] 按鈕。

    - 在功能表列上，選擇 [ **Debug**  >  **停止調試**]。

    - 使用鍵盤，然後按 **Shift** + **F5**。

    - 選擇 **Form1** 視窗左上角的 [ **X** ] 按鈕。

    > [!NOTE]
    > 當您從 IDE 內執行您的應用程式時，它會呼叫偵錯工具，因為您通常會在應用程式中找出並修正 (錯誤) 的 bug。 雖然此應用程式很小，而且還沒有這麼做，但它仍然是真正的程式。 您遵循相同程序執行和偵錯其他程式。 若要深入了解偵錯，請參閱[偵錯工具簡介](../debugger/debugger-feature-tour.md)。

## <a name="next-steps"></a>下一步

* 若要移至下一個教學課程步驟，請參閱 **[步驟3：設定您的表單內容](../ide/step-3-set-your-form-properties.md)**。

* 若要回到上一個教學課程步驟，請參閱 [步驟1：建立 Windows Forms 應用程式專案](../ide/step-1-create-a-windows-forms-application-project.md)。

## <a name="see-also"></a>另請參閱

* [教學課程2：建立計時的數學測驗](tutorial-2-create-a-timed-math-quiz.md)
* [教學課程3：建立配對遊戲](tutorial-3-create-a-matching-game.md)
