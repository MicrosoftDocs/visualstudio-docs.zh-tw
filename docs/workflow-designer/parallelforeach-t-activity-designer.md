---
title: ParallelForEach &lt; T &gt; 活動設計工具
description: 在工作流程設計工具中，您將瞭解 ParallelForEach <T> 活動如何列舉集合的元素，並針對集合的每個專案平行執行內嵌語句。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e732c6d9d791d789471c49a319ab9945fdd5dc06
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996171"
---
# <a name="parallelforeach-activity-designer"></a>ParallelForEach 活動設計工具

<xref:System.Activities.Statements.ParallelForEach%601> 活動會列舉集合的項目，並且平行執行集合中各個項目的內嵌陳述式，而這是同一個執行緒上的非同步處理。 如果預期此活動的子活動會進入閒置狀態，請使用這個流量控制活動代替 <xref:System.Activities.Statements.Sequence> 活動。

<xref:System.Activities.Statements.ParallelForEach%601>活動具有 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> 屬性，該屬性包含 Visual Basic 運算式指定的使用者。 在各個分支完成之後，<xref:System.Activities.Statements.ParallelForEach%601> 活動會評估這個屬性。 如果評估為 **true**，則 <xref:System.Activities.Statements.ParallelForEach%601> 活動會完成，而不會執行其他分支。 如果 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> 未評估為 **true**，則 <xref:System.Activities.Statements.ParallelForEach%601> 活動會在所有子活動都已完成時完成。

## <a name="the-parallelforeacht-activity"></a>ParallelForEach<T \> 活動

<xref:System.Activities.Statements.ParallelForEach%601> 列舉其值，並 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 針對其所列舉的每個值排程。 只會排程 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>。 主體執行的方式取決於 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 是否變成閒置。

如果 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 沒有變成閒置，就會依相反順序執行，因為排程的活動會做為一個堆疊處理，所以最後排程的活動會最先執行。 例如，如果您 {1,2,3,4} 在中有集合 <xref:System.Activities.Statements.ParallelForEach%601> ，並使用 **WriteLine** 做為主體來寫入值。您已在主控台中列印4、3、2、1。 這是因為 **WriteLine** 未進入閒置狀態，因此在排程4個 **WriteLine** 活動之後，它們會使用堆疊行為來執行， (先在最後一次的) 。

但是，如果您在 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 中有活動可以變成閒置，像是 <xref:System.ServiceModel.Activities.Receive> 活動或 <xref:System.Activities.Statements.Delay> 活動。 那麼，則不需要等候它們完成。 <xref:System.Activities.Statements.ParallelForEach%601> 會移至下一個排程的主體活動，且會嘗試執行此活動。 如果該活動也變成閒置，<xref:System.Activities.Statements.ParallelForEach%601> 就會再移至下一個主體活動。

### <a name="using-the-parallelforeacht-activity-designer"></a>使用 ParallelForEach \<T> 活動設計工具

存取 [工具箱] 的 [**控制流程**] 分類中的 [ **ParallelForEach \<T>** ] 活動設計 **工具**。

[ **ParallelForEach \<T>** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到工作流程設計工具介面上，通常用來放置活動設計工具的任一處，例如在 [ **Sequence** ] 活動設計工具內部。 將它放入工作流程設計工具之後，它會建立 <xref:System.Activities.Statements.ParallelForEach%601> 活動，此活動預設包含 <xref:System.Activities.Activity.DisplayName%2A> 的 **ParallelForEach<Int32 \> 。**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach \> 工作流程設計工具中<T 屬性

下表顯示最為實用的 <xref:System.Activities.Statements.ParallelForEach%601> 活動屬性，並且說明它們在設計工具中的使用方式。

|屬性名稱|必要|使用量|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|指定活動設計工具在標頭中的易記顯示名稱。 預設值為 **ParallelForEach \<Int32>**。 您可以選擇性地在 **屬性** 方格中或直接在活動設計工具標頭上編輯此值。|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|否|集合中每個項目要執行的活動。 若要加入 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 活動，請從 [工具箱 **] 將** 活動拖放到 [ **ParallelForEach \<T>** ] 活動設計工具的 [內文] 方塊中，並在 [在此放置活動] 提示文字。|
|**TypeArgument**|是|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>泛型參數 *T* 所指定集合中的專案類型。根據預設， **TypeArgument** 設定為 **Int32**。 若要變更 **ParallelForEach<T \>** 活動設計工具中的型別 t，請變更屬性方格中 [ **TypeArgument** ] 下拉式方塊的值。|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|是|要重複項目的集合。 若要設定 <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> ，請在 [ **\> ForEach<T** 活動設計工具] 的 [**值**] 方塊中輸入 Visual Basic 運算式，其中包含提示文字 [輸入 VB 運算式] 或 [**屬性**] 視窗的 [**值**] 方塊中。|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||在每個反覆運算完成之後評估。 如果評估為 true，則會取消已排程的擱置中反覆運算。 如果並未設定此屬性，則會執行所有已排程的陳述式，直到完成為止。|

依預設，迴圈 Iterator 會命名為 item。 您可以在 [ **ParallelForEach \<T>** ] 活動設計工具的 [ **ForEach** ] 方塊中變更 iterator 變數的名稱。 迴圈 Iterator 可用在 <xref:System.Activities.Statements.ParallelForEach%601> 活動子系中的運算式。

## <a name="see-also"></a>另請參閱

- [序列](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [控制流程](../workflow-designer/control-flow-activity-designers.md)