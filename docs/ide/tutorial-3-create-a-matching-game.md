---
title: 教學課程 3：建立配對遊戲
ms.date: 10/16/2019
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
ms.topic: tutorial
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 619c21f4878f2e421ee5ac5ea76a68cd6e6bc337
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579714"
---
# <a name="tutorial-3-create-a-matching-game"></a>教學課程 3：建立配對遊戲

在本教學課程中，您會建置一個配對遊戲，而遊戲玩家必須配對隱藏的圖示。

> [!NOTE]
> 本教學課程涵蓋C#和 Visual Basic，因此請專注于您所使用之程式設計語言的特定資訊。

本教學課程將逐步引導您完成下列工作：

- 在 <xref:System.Collections.Generic.List%601> 物件中儲存物件 (例如圖示)。

- 使用中C#的 `foreach` 迴圈或 Visual Basic 中的 `For Each` 迴圈，逐一查看清單中的專案。

- 使用參考變數追蹤表單的狀態。

- 建置您可以搭配多個物件使用的事件處理常式來回應事件。

- 讓計時器倒數計時，然後讓計時器於啟動後剛好引發一個事件。

當您完成時，您的應用程式看起來應該類似下圖：

![您在本教學課程中建立的遊戲](../ide/media/express_finishedgame.png)

## <a name="tutorial-links"></a>教學課程的連結

|Title|描述|
|-----------|-----------------|
|[步驟 1：建立專案並將資料表新增至表單](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|從建立專案並新增 `TableLayoutPanel` 控制項，讓控制項正確對齊開始。|
|[步驟 2：新增隨機物件和圖示清單](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|加入 `Random` 物件和 `List` 物件，以建立圖示清單。|
|[步驟 3：將隨機圖示指派給每個標籤](../ide/step-3-assign-a-random-icon-to-each-label.md)|將圖示隨機指派給 `Label` 控制項；因此，每個遊戲是不同的。|
|[步驟 4：將 Click 事件處理常式新增至每個標籤](../ide/step-4-add-a-click-event-handler-to-each-label.md)|加入 `Click` 事件處理常式，以變更已按下標籤的色彩。|
|[步驟 5：加入標籤參考](../ide/step-5-add-label-references.md)|加入參考變數，以追蹤已按一下的標籤。|
|[步驟 6：新增計時器](../ide/step-6-add-a-timer.md)|將計時器加入至表單，追蹤遊戲已經過的時間。|
|[步驟 7：讓配對保持可見](../ide/step-7-keep-pairs-visible.md)|如果已選取相符的配對，請讓圖示配對維持可見狀態。|
|[步驟 8：新增方法以驗證玩家是否贏了](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|加入 `CheckForWinner()` 方法以驗證玩家是否贏了。|
|[步驟 9：嘗試其他功能](../ide/step-9-try-other-features.md)|嘗試其他功能，例如變更圖示和色彩、加上格線，以及加入音效。 試著讓戲局變大並調整計時器。|

另外還有絕佳的免費影片學習資源可供您使用。 若要深入瞭解中的C#程式設計，請參閱[ C#基本概念：適用于絕對初學者的開發](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners)。 若要深入了解 Visual Basic 中的程式設計，請參閱 [Visual Basic 基礎：徹底初學者開發](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners) \(英文\)。

## <a name="next-steps"></a>後續步驟

若要開始本教學課程，請從 **[步驟1：建立專案並將資料表新增至表單](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)** 開始。

## <a name="see-also"></a>另請參閱

* [其他C#教學課程](/visualstudio/get-started/csharp/)
* [Visual Basic 教學課程](/visualstudio/get-started/visual-basic/)
* [C++教程](/cpp/get-started/tutorial-console-cpp)
