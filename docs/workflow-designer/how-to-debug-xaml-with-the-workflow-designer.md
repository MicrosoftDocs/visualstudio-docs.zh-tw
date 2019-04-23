---
title: 工作流程設計工具-如何：使用工作流程設計工具對 XAML 進行偵錯
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: cdbf5fa21c8fcf9069db9a7348d4ed576fc342c5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60065879"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>HOW TO：使用工作流程設計工具對 XAML 進行偵錯

工作流程是根據 XAML 所定義的。 工作流程的 UI 呈現方式，乃是建立在定義該工作流程的 XAML 樹狀結構上。 偵錯的體驗是類似於偵錯工作流程設計工具中的工作流程。 比方說，在偵錯 XAML，時 [區域變數]、 [監看式] 和 [執行緒] 視窗的運作方式相同偵錯工作流程設計工具中所顯示的一樣。 此外，在 XAML 偵錯期間的呼叫堆疊檢視，也是工作流程執行流程的逐行階層架構檢視。

> [!NOTE]
> 如果為工作流程的 XAML 與活動位於同一個組件中，則不會包含類別名稱中的組件部分。 沒有類別 (活動) 名稱的這個部分，就不能在執行階段載入 XAML。 不建議在與主要專案的同一個命名空間中定義活動，否則，XAML 在設計工具中編輯之後必須手動編輯。

## <a name="to-debug-workflow-xaml"></a>若要進行工作流程 XAML 偵錯

1. Visual Studio 中開啟的工作流程或活動專案。

2. 或多個您想要偵錯中所述的活動上設定中斷點[How to:在工作流程中設定中斷點](../workflow-designer/how-to-set-breakpoints-in-workflows.md)。

3. 以滑鼠右鍵按一下包含您的工作流程定義和選取的.xaml 檔案**檢視程式碼**。 在設計檢視中設定中斷點的活動之後，您會看到該活動 XAML 項目宣告的同一行上顯示中斷點。

4. 叫用偵錯工具，如中所述[偵錯工作流程](debugging-workflows-with-the-workflow-designer.md)。

5. 當程式碼執行到您的其中一個中斷點時，該中斷點關聯的 XAML 項目會出現醒目顯示。 若要移動到下一個中斷點，請使用**F10**或是**F11**索引鍵。

## <a name="see-also"></a>另請參閱

- [如何：在工作流程中設定中斷點](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [偵錯工作流程](debugging-workflows-with-the-workflow-designer.md)