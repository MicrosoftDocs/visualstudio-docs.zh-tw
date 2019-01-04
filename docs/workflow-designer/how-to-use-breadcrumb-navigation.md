---
title: 工作流程設計工具-如何：使用階層連結巡覽
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3620c1d39413d3c7e2f1339fcc856d2d8421255d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53963880"
---
# <a name="how-to-use-breadcrumb-navigation"></a>HOW TO：使用階層連結巡覽

有三種主要的方法，若要變更的一組會顯示在工作流程設計工具的活動：

1.  按兩下來向內切入子活動。

2.  按一下階層連結列上的按鈕來巡覽至祖系活動。

3.  就地展開或摺疊活動。

## <a name="using-breadcrumb-navigation"></a>使用階層連結巡覽

1.  按兩下已按下的活動變更根活動的工作流程設計工具的活動。 按下的活動會完全展開根目錄和其祖系會顯示在階層連結列中。 有時，這會稱為向內切入或向外切出活動。

2.  若要巡覽至目前根活動的祖系，請按一下階層連結列上的活動。

## <a name="expanding-or-collapsing-an-activity-in-place"></a>就地展開或摺疊活動

1.  按一下活動上的＞形箭號，即可就地展開或摺疊活動。

2.  按一下按鈕而變更展開狀態時，展開的新狀態會儲存於 XAML。

    > [!WARNING]
    > 並非所有活動都可就地展開。 無法就地展開活動的情況有兩種：父活動不允許就地展開子活動，(例如，流程圖中的活動無法就地展開)，或活動設計工具不允許將本身就地展開。 雖然所有的工作流程設計工具中包含的活動設計工具都發生後者的情況時，某些自訂活動可能會出現此行為。

## <a name="expanding-all-or-collapsing-all-activities"></a>全部展開或全部摺疊活動

1.  使用**全部展開**並**全部摺疊**展開或摺疊目前階層連結根目錄下的活動的所有使用者介面中的按鈕。 請注意，全部展開和全部摺疊都是全域狀態。 這表示，當您變更根活動使用軌跡瀏覽，全部展開或摺疊所有狀態一直保存，直到您按一下**還原**。

2.  您已套用全部展開或摺疊所有狀態之後，您可以按一下**還原**按鈕返回查看先前套用至每個活動的狀態。

    > [!WARNING]
    > 如果某個活動，這類<xref:System.Activities.Statements.Flowchart>，已選擇共就地展開、 功能與相關聯**全部展開**並**全部摺疊**按鈕已停用**流程圖**設計工具。 如需詳細資訊**流程圖**設計工具，請參閱[流程圖](../workflow-designer/flowchart-activity-designer.md)主題。

    > [!WARNING]
    > 全部展開中也有特殊效果**交換器**並**TryCatch**活動設計工具。 當您按一下 **全部展開**，顯示的切換案例與所有的 try/catch/finally 區塊。 按一下 **還原**或是**全部摺疊**傳回這些設計工具，為其預設狀態，您可以從中按一下個別案例/區塊來檢視其內容。