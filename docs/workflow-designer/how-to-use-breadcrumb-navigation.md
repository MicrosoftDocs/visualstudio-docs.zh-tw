---
title: 如何： 使用階層連結巡覽 |Microsoft 文件
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97c88a8c47bfaa2e1ccd135baec95f19a49c4e5a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-breadcrumb-navigation"></a>HOW TO：使用階層連結巡覽

有三種主要的方法，若要變更的一組 Windows 工作流程設計工具中顯示的活動：

1.  按兩下來向內切入子活動。

2.  按一下階層連結列上的按鈕來巡覽至祖系活動。

3.  就地展開或摺疊活動。

### <a name="using-breadcrumb-navigation"></a>使用階層連結巡覽

1.  按兩下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 活動，從根活動變更為按下後的活動。 按下後的活動就會完全於根目錄展開，而且其祖系會顯示於階層連結列。 有時，這會稱為向內切入或向外切出活動。

2.  若要巡覽至目前根活動的祖系，請按一下階層連結列上的活動。

### <a name="expanding-or-collapsing-an-activity-in-place"></a>就地展開或摺疊活動

1.  按一下活動上的＞形箭號，即可就地展開或摺疊活動。

2.  按一下按鈕而變更展開狀態時，展開的新狀態會儲存於 XAML。

    > [!WARNING]
    > 並非所有活動都可就地展開。 無法就地展開活動的情況有兩種：父活動不允許就地展開子活動，(例如，流程圖中的活動無法就地展開)，或活動設計工具不允許將本身就地展開。 雖然包含於 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 的活動設計工具都不會發生後者的情況，但是某些自訂活動也許會有這種情況。

### <a name="expanding-all-or-collapsing-all-activities"></a>全部展開或全部摺疊活動

1.  使用**全部展開**和**全部摺疊**展開或摺疊目前階層連結根目錄下的所有活動的使用者介面中的按鈕。 請注意，全部展開和全部摺疊都是全域狀態。 這表示，當您變更根活動使用階層連結巡覽，全部展開或摺疊的所有狀態一直保存，直到您按一下**還原**。

2.  套用全部展開或摺疊的所有狀態之後，您可以按一下**還原**按鈕，以返回查看先前套用至每個活動的狀態。

    > [!WARNING]
    > 如果某個活動，例如<xref:System.Activities.Statements.Flowchart>，已選擇不就地展開，功能與相關聯**全部展開**和**全部摺疊**上已停用按鈕**流程圖**設計工具。 如需有關**流程圖**設計工具，請參閱[流程圖](../workflow-designer/flowchart-activity-designer.md)主題。

    > [!WARNING]
    > 全部展開中也有特殊效果**交換器**和**TryCatch**活動設計工具。 當您按一下**全部展開**，顯示的切換案例與所有的 try/catch/finally 區塊。 按一下**還原**或**全部摺疊**返回這些設計工具恢復預設狀態，您可從中按一下個別的案例/區塊來檢視其內容。