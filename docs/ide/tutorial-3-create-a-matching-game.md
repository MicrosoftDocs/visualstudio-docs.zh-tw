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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579714"
---
# <a name="tutorial-3-create-a-matching-game"></a>教學課程 3：建立配對遊戲

在本教學課程中，您會建置一個配對遊戲，而遊戲玩家必須配對隱藏的圖示。

> [!NOTE]
> 本教程將介紹 C# 和 Visual Basic，因此請關注特定于您使用的程式設計語言的資訊。

本教程將引導您完成以下任務：

- 在 <xref:System.Collections.Generic.List%601> 物件中儲存物件 (例如圖示)。

- 使用`foreach`C# 中的迴圈或`For Each`Visual Basic 中的迴圈反覆運算清單中的項。

- 使用參考變數追蹤表單的狀態。

- 建置您可以搭配多個物件使用的事件處理常式來回應事件。

- 讓計時器倒數計時，然後讓計時器於啟動後剛好引發一個事件。

完成後，你的應用應類似于下圖：

![您在本教學課程中建立的遊戲](../ide/media/express_finishedgame.png)

## <a name="tutorial-links"></a>教學課程的連結

|Title|描述|
|-----------|-----------------|
|[步驟 1：建立專案並將資料表新增至表單](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|從建立專案並新增 `TableLayoutPanel` 控制項，讓控制項正確對齊開始。|
|[第 2 步：添加隨機物件和圖示清單](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|加入 `Random` 物件和 `List` 物件，以建立圖示清單。|
|[步驟 3：將隨機圖示指派給每個標籤](../ide/step-3-assign-a-random-icon-to-each-label.md)|將圖示隨機指派給 `Label` 控制項；因此，每個遊戲是不同的。|
|[步驟 4：將按一下事件處理常式添加到每個標籤](../ide/step-4-add-a-click-event-handler-to-each-label.md)|加入 `Click` 事件處理常式，以變更已按下標籤的色彩。|
|[步驟 5：加入標籤參考](../ide/step-5-add-label-references.md)|加入參考變數，以追蹤已按一下的標籤。|
|[第 6 步：添加計時器](../ide/step-6-add-a-timer.md)|將計時器加入至表單，追蹤遊戲已經過的時間。|
|[第 7 步：保持對可見](../ide/step-7-keep-pairs-visible.md)|如果已選取相符的配對，請讓圖示配對維持可見狀態。|
|[步驟 8：添加一種方法來驗證玩家是否獲勝](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|加入 `CheckForWinner()` 方法以驗證玩家是否贏了。|
|[第 9 步：嘗試其他功能](../ide/step-9-try-other-features.md)|嘗試其他功能，例如變更圖示和色彩、加上格線，以及加入音效。 試著讓戲局變大並調整計時器。|

也有偉大的，免費的視頻學習資源可供你使用。 要瞭解有關 C# 中程式設計的更多詳細資訊，請參閱[C# 基礎知識：絕對初學者的開發](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners)。 若要深入了解 Visual Basic 中的程式設計，請參閱 [Visual Basic 基礎：徹底初學者開發](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners) \(英文\)。

## <a name="next-steps"></a>後續步驟

要開始本教程，請從步驟 1 開始**[：創建專案並將表添加到表單](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)** 中。

## <a name="see-also"></a>另請參閱

* [更多 C# 教程](/visualstudio/get-started/csharp/)
* [Visual Basic 教學課程](/visualstudio/get-started/visual-basic/)
* [C++教程](/cpp/get-started/tutorial-console-cpp)
