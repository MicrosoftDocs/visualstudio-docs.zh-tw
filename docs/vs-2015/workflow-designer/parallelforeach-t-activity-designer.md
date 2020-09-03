---
title: ParallelForEach &lt; T &gt; 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c659e941a8503a0d5ff601fea23fcec69b2bbcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672606"
---
# <a name="parallelforeachlttgt-activity-designer"></a>ParallelForEach &lt; T &gt; 活動設計工具
<xref:System.Activities.Statements.ParallelForEach%601> 活動會列舉集合的項目，並且平行執行集合中各個項目的內嵌陳述式，而這是同一個執行緒上的非同步處理。 如果預期此活動的子活動會進入閒置狀態，請使用這個流量控制活動代替 <xref:System.Activities.Statements.Sequence> 活動。

 <xref:System.Activities.Statements.ParallelForEach%601> 活動有一個 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> 屬性，其中包含使用者指定的 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 運算式。 在各個分支完成之後，<xref:System.Activities.Statements.ParallelForEach%601> 活動會評估這個屬性。 如果評估為 **true**，則 <xref:System.Activities.Statements.ParallelForEach%601> 活動會完成，而不會執行其他分支。 如果 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> 未評估為 **true**，則 <xref:System.Activities.Statements.ParallelForEach%601> 活動會在所有子活動都已完成時完成。

## <a name="the-parallelforeacht-activity"></a>ParallelForEach \<T> 活動
 <xref:System.Activities.Statements.ParallelForEach%601> 列舉其值，並 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 針對其所列舉的每個值排程。 只會排程 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>。 主體執行的方式取決於 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 是否變成閒置。

 如果 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 沒有變成閒置，就會依相反順序執行，因為排程的活動會做為一個堆疊處理，所以最後排程的活動會最先執行。 例如，如果您 {1,2,3,4} 在中有集合 <xref:System.Activities.Statements.ParallelForEach%601> ，並使用 **WriteLine** 做為主體來寫入值。您已在主控台中列印4、3、2、1。 這是因為 **WriteLine** 未進入閒置狀態，因此在排程4個 **WriteLine** 活動之後，它們會使用堆疊行為來執行， (先在最後一次的) 。

 但是，如果您在 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 中有活動可以變成閒置，像是 <xref:System.ServiceModel.Activities.Receive> 活動或 <xref:System.Activities.Statements.Delay> 活動。 那麼，則不需要等候它們完成。 <xref:System.Activities.Statements.ParallelForEach%601> 會移至下一個排程的主體活動，且會嘗試執行此活動。 如果該活動也變成閒置，<xref:System.Activities.Statements.ParallelForEach%601> 就會再移至下一個主體活動。

### <a name="using-the-parallelforeacht-activity-designer"></a>使用 ParallelForEach \<T> 活動設計工具
 [ **ParallelForEach \<T> ** ] 活動設計**工具**位於 [工具箱] 的 [**控制流程**] 類別中，若要存取，請按一下 (左側的 [**工具箱**] 索引標籤， [!INCLUDE[wfd2](../includes/wfd2-md.md)] 也可以從 [ **View** ] 功能表選取 [**工具列**]，或按 CTRL + ALT + X。 ) 

 [ **ParallelForEach \<T> ** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到介面上通常用來 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 放置活動設計工具的任一處，例如在 [ **Sequence** ] 活動設計工具內部。 將它放入之後 [!INCLUDE[wfd2](../includes/wfd2-md.md)] ，它會建立 <xref:System.Activities.Statements.ParallelForEach%601> 活動，此活動預設包含 <xref:System.Activities.Activity.DisplayName%2A> ParallelForEach 的 ** \<Int32> 。**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>\<T>工作流程設計工具中的 ParallelForEach 屬性
 下表顯示最為實用的 <xref:System.Activities.Statements.ParallelForEach%601> 活動屬性，並且說明它們在設計工具中的使用方式。

|屬性名稱|必要|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|否|指定活動設計工具在標頭中的易記顯示名稱。 預設值為**ParallelForEach \<Int32> **。 您可以選擇性地在 **屬性** 方格中或直接在活動設計工具標頭上編輯此值。|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|否|集合中每個項目要執行的活動。 若要加入 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 活動，請從 [工具箱 **] 將**活動拖放到 [ **ParallelForEach \<T> ** ] 活動設計工具的 [內文] 方塊中，並在 [在此放置活動] 提示文字。|
|**TypeArgument**|是|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>泛型參數*T*所指定集合中的專案類型。根據預設， **TypeArgument**設定為**Int32**。 若要變更**ParallelForEach \<T> **活動設計工具中的型別 T，請變更屬性方格中 [ **TypeArgument** ] 下拉式方塊的值。|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|是|要重複項目的集合。 若要設定 <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> ，請在 [ForEach] 活動設計工具的 [ [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ** \<T> ForEach** ] 活動設計工具的 [**值**] 方塊中輸入運算式，並在 [**屬性**] 視窗的 [**值**] 方塊中輸入提示文字。|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||在每個反覆運算完成之後評估。 如果評估為 true，則會取消已排程的擱置中反覆運算。 如果並未設定此屬性，則會執行所有已排程的陳述式，直到完成為止。|

 依預設，迴圈 Iterator 會命名為 item。 您可以在 [ **ParallelForEach \<T> ** ] 活動設計工具的 [ **ForEach** ] 方塊中變更 iterator 變數的名稱。 迴圈 Iterator 可用在 <xref:System.Activities.Statements.ParallelForEach%601> 活動子系中的運算式。

## <a name="see-also"></a>另請參閱
 [順序](../workflow-designer/sequence-activity-designer.md)[平行](../workflow-designer/parallel-activity-designer.md)[控制流程](../workflow-designer/control-flow-activity-designers.md)