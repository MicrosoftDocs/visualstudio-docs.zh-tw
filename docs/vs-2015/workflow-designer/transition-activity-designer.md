---
title: 轉換活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Transition.UI
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
caps.latest.revision: 7
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 446a78e706e1ba3cfd650418a9d329b62b330de8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606917"
---
# <a name="transition-activity-designer"></a>轉換活動設計工具
<xref:System.Activities.Statements.Transition> 表示在兩個狀態之間轉換。

## <a name="using-the-transition-activity-designer"></a>使用 Transition 活動設計工具
 Transition 活動設計工具允許您設定兩個狀態之間的轉換。

### <a name="transition-properties-in-the-workflow-designer"></a>工作流程設計工具中的 Transition 屬性
 下表顯示可使用工作流程設計工具設定的 <xref:System.Activities.Statements.Transition> 屬性，並說明如何在設計工具中使用它們。

|屬性名稱|必要項|使用量|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Transition> 活動設計工具的易記名稱。 預設值是**T1**。 這個值可以在這些位置進行編輯：屬性方格、展開的轉換設計工具標頭，以及展開的轉換設計工具內動作區段的標頭。 <xref:System.Activities.Activity.DisplayName%2A> 可用於階層連結巡覽，顯示在工作流程設計工具的頂端。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.Transition.Condition%2A>|False|如果有的話，會指定必須評估為**True**的運算式，才會將控制權傳遞至目的地狀態。 這個條件可以在屬性方格和展開的轉換設計工具中編輯。 共用轉換中的多個條件是以它們在轉換設計工具中的出現順序接受評估。 **注意：** 請注意，如果轉換的 <xref:System.Activities.Statements.Transition.Condition%2A> 評估為**false** （或共用觸發程式轉換的所有條件都評估為**false**），則不會進行轉換，而且會重新排程所有從狀態轉換的觸發程式。 由於設定條件的方式，在本教學課程中不會發生這種情況 (我們對於猜測是否正確有具體的動作)。|
|**Source**|True|表示此轉換所源自的狀態。 按一下來源狀態的名稱，可將設計工具檢視切換到該狀態的展開檢視。 當轉換已建立且不能變更時會設定此值。|
|<xref:System.Activities.Statements.Transition.Trigger%2A>|False|指定此活動，活動完成時會起始轉換。 若要設定此活動，請從 [**工具箱**] 將活動拖放到轉換的 [**觸發**程式] 區段。|
|<xref:System.Activities.Statements.Transition.Action%2A>|False|指定當觸發程式活動完成且 <xref:System.Activities.Statements.Transition.Condition%2A> （如果有的話）評估為**true**時，所執行的活動。 執行來源狀態的 <xref:System.Activities.Statements.State.Exit%2A> 活動 (如果有的話) 之後，轉換到目的狀態時會執行此活動。 當轉換設計工具展開時，可以從 [**工具箱**] 拖曳活動並放到轉換的 [**動作**] 區段上，藉此設定此值。 單一轉換可以有多個動作。 個別的動作可以展開和收縮，而且當轉換有多個動作時，可以按一下出現在動作上的上下箭號來加以排序。|
|**目的地**|True|表示轉換完成之後狀態機器轉換到的狀態。 這個對應至物件模型中轉換的 <xref:System.Activities.Statements.Transition.To%2A> 屬性。 按一下目的狀態的名稱，可將設計工具檢視切換到該狀態的展開檢視。 當轉換已建立並可用拖曳箭頭 (其將轉換連接至設計工具中的目的狀態) 的方式進行變更時，會設定這個值。|

### <a name="creating-transitions"></a>建立轉換
 轉換可由這些方式建立：從某個狀態將線條拖曳到另一個狀態，或將狀態放到三角形上，當某個狀態被拖曳到另一個狀態上方時會出現此三角形。 若要以拖曳的方式來建立轉換，將滑鼠停留在來源狀態的邊緣，並將線條從源狀態拖曳到目的狀態。 若要以放置的方式來建立轉換，拖曳目的狀態並停留在來源狀態上方，然後放到來源狀態周圍四個三角形的其中一個。 目的地狀態可以是從 [工具箱] 拖曳的新狀態，或是從工作流程設計**工具**拖曳的現有狀態。

> [!NOTE]
> 狀態機器中的單一狀態最多可以有 76 個以工作流程設計工具來建立的轉換。 針對在設計工具以外建立的工作流程，狀態的轉換數目上限僅受制於系統資源。

 共用觸發轉換是一組共用相同觸發事件的轉換。 共用觸發程序允許對目的狀態的條件式進展，根據的是運算式的評估結果，此運算式是針對多個共用通用觸發事件的轉換所設定。 若要將其他動作加入到轉換，並建立共用轉換，請按一下指出所要之轉換起始點的圓形，然後將它拖曳到所要的狀態。 新的轉換會與初始轉換共用相同的觸發程序，但擁有唯一的條件和動作。 您也可以從轉換設計工具內建立共用轉換，方法是按一下轉換設計工具底部的 [**新增共用觸發程式轉換**]，然後從可用的狀態選取所需的目標狀態**以進行**連線下拉式。

## <a name="see-also"></a>請參閱
 [StateMachine](../workflow-designer/statemachine-activity-designer.md) [FinalState](../workflow-designer/finalstate-activity-designer.md) [狀態](../workflow-designer/state-activity-designer.md)