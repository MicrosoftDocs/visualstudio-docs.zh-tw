---
title: 工作流程設計工具-如何：使用階層連結流覽
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7a851ea074a78349c9e52ef127bf2814d203bf5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650319"
---
# <a name="how-to-use-breadcrumb-navigation"></a>HOW TO：使用階層連結巡覽

有三種主要方式可變更工作流程設計工具中顯示的活動集合：

1. 按兩下來向內切入子活動。

2. 按一下階層連結列上的按鈕來巡覽至祖系活動。

3. 就地展開或摺疊活動。

## <a name="using-breadcrumb-navigation"></a>使用階層連結巡覽

1. 按兩下工作流程設計工具的活動，將根活動變更為按下的活動。 然後，按下的活動會在根節點完全展開，而其祖系會顯示在階層連結列中。 有時，這會稱為向內切入或向外切出活動。

2. 若要巡覽至目前根活動的祖系，請按一下階層連結列上的活動。

## <a name="expanding-or-collapsing-an-activity-in-place"></a>就地展開或摺疊活動

1. 按一下活動上的＞形箭號，即可就地展開或摺疊活動。

2. 按一下按鈕而變更展開狀態時，展開的新狀態會儲存於 XAML。

    > [!WARNING]
    > 並非所有活動都可就地展開。 無法就地展開活動的情況有兩種：父活動不允許就地展開子活動，(例如，流程圖中的活動無法就地展開)，或活動設計工具不允許將本身就地展開。 雖然工作流程設計工具中未包含任何活動設計工具具有後者的行為，但某些自訂活動可能會出現這種行為。

## <a name="expanding-all-or-collapsing-all-activities"></a>全部展開或全部摺疊活動

1. 使用使用者介面中的 [**全部展開**] 和 [**全部**折迭] 按鈕，展開或折迭目前階層連結根目錄下的所有活動。 請注意，全部展開和全部摺疊都是全域狀態。 這表示當您使用階層連結流覽來變更根活動時，[全部展開] 或 [全部折迭] 狀態會一直保留，直到您按一下 [**還原**] 為止。

2. 套用全部展開或全部折迭的狀態之後，您可以按一下出現的 [**還原**] 按鈕，返回查看先前套用至每個活動的狀態。

    > [!WARNING]
    > 如果某個活動（例如 <xref:System.Activities.Statements.Flowchart>）已選擇不就地展開，則會停用 [**流程圖**] 設計工具上與 [全部**展開**] 和 [**全部**折迭] 按鈕相關聯的功能。 如需**流程圖**設計工具的詳細資訊，請參閱[流程圖](../workflow-designer/flowchart-activity-designer.md)主題。

    > [!WARNING]
    > [全部展開] 在 [ **Switch** ] 和 [ **TryCatch** ] 活動設計工具中也有特殊效果。 當您按一下 [**全部展開**] 時，就會顯示所有的切換案例和所有的 try/catch/finally 區塊。 按一下 [**還原**] 或 [**全部**折迭] 會將這些設計工具傳回預設狀態，您可以在其中按一下個別的案例/區塊來查看其內容。