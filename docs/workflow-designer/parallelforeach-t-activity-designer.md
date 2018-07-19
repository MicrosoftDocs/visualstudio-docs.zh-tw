---
title: 工作流程設計工具-ParallelForEach&lt;T&gt;活動設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 53b8a8790cfa4f4e1f962fa5e6ce82b62781430f
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756902"
---
# <a name="parallelforeach-activity-designer"></a>ParallelForEach 活動設計工具

<xref:System.Activities.Statements.ParallelForEach%601> 活動會列舉集合的項目，並且平行執行集合中各個項目的內嵌陳述式，而這是同一個執行緒上的非同步處理。 如果預期此活動的子活動會進入閒置狀態，請使用這個流量控制活動代替 <xref:System.Activities.Statements.Sequence> 活動。

<xref:System.Activities.Statements.ParallelForEach%601>活動具有<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>屬性，其中包含使用者指定 Visual Basic 運算式。 在各個分支完成之後，<xref:System.Activities.Statements.ParallelForEach%601> 活動會評估這個屬性。 如果評估為 **，則為 true**，然後在<xref:System.Activities.Statements.ParallelForEach%601>活動完成且沒有執行其他分支。 如果<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>不會評估 **，則為 true**，然後在<xref:System.Activities.Statements.ParallelForEach%601>活動完成的所有子活動完成時。

## <a name="the-parallelforeacht-activity"></a>ParallelForEach < T\>活動

<xref:System.Activities.Statements.ParallelForEach%601> 會列舉其值，並且為列舉的每一個值排程 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>。 只會排程 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>。 主體執行的方式取決於 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 是否變成閒置。

如果 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 沒有變成閒置，就會依相反順序執行，因為排程的活動會做為一個堆疊處理，所以最後排程的活動會最先執行。 例如，如果您有一堆{1,2,3,4}中<xref:System.Activities.Statements.ParallelForEach%601>並用**WriteLine**做為主體將值寫出。主控台會有 4, 3, 2, 1 列印出來。 這是因為**WriteLine**沒有變成閒置，4 之後**WriteLine**活動已排程、 他們使用堆疊行為來執行 （第一個在最後一個外）。

但是，如果您在 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 中有活動可以變成閒置，像是 <xref:System.ServiceModel.Activities.Receive> 活動或 <xref:System.Activities.Statements.Delay> 活動。 那麼，則不需要等候它們完成。 <xref:System.Activities.Statements.ParallelForEach%601> 會移至下一個排程的主體活動，且會嘗試執行此活動。 如果該活動也變成閒置，<xref:System.Activities.Statements.ParallelForEach%601> 就會再移至下一個主體活動。

### <a name="using-the-parallelforeacht-activity-designer"></a>使用 ParallelForEach\<T > 活動設計工具

存取權**ParallelForEach\<T >** 中的活動設計工具**控制流程**分類**工具箱**。

**ParallelForEach\<T >** 活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面，只要活動設計工具通常用來放置，如例如，內部**順序**活動設計工具。 後放入工作流程設計工具，它會建立<xref:System.Activities.Statements.ParallelForEach%601>活動，其中預設包含<xref:System.Activities.Activity.DisplayName%2A>的**ParallelForEach < Int32\>。**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach < T\> Workflow Designer 中的屬性

下表顯示最為實用的 <xref:System.Activities.Statements.ParallelForEach%601> 活動屬性，並且說明它們在設計工具中的使用方式。

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定活動設計工具在標頭中的易記顯示名稱。 預設值是**ParallelForEach\<Int32 >**。 值可以在中選擇性地編輯**屬性**方格或直接在活動設計工具標頭。|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|集合中每個項目要執行的活動。 若要新增<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>活動，請從工具箱拖曳到**主體**方塊**ParallelForEach\<T >** 活動設計工具提示文字 「 置放活動 」 與。|
|**TypeArgument**|True|中的項目型別<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>一般參數所指定的集合*T*。根據預設， **TypeArgument**設為**Int32**。 若要變更中的型別 T **ParallelForEach < T\>** 活動設計工具，變更的值**TypeArgument**屬性方格中的下拉式方塊。|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|True|要重複項目的集合。 若要設定<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>，輸入在 Visual Basic 運算式**值**方塊**ForEach < T\>** 活動設計工具提示文字 「 輸入 VB 運算式 」 的方塊中，或在**值** 方塊**屬性**視窗。|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||在每個反覆運算完成之後評估。 如果評估為 true，則會取消已排程的擱置中反覆運算。 如果並未設定此屬性，則會執行所有已排程的陳述式，直到完成為止。|

依預設，迴圈 Iterator 會命名為 item。 您可以變更其迭代器變數的名稱**ForEach**方塊中**ParallelForEach\<T >** 活動設計工具。 迴圈 Iterator 可用在 <xref:System.Activities.Statements.ParallelForEach%601> 活動子系中的運算式。

## <a name="see-also"></a>另請參閱

- [順序](../workflow-designer/sequence-activity-designer.md)
- [平行](../workflow-designer/parallel-activity-designer.md)
- [控制流程](../workflow-designer/control-flow-activity-designers.md)