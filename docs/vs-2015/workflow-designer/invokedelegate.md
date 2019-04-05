---
title: InvokeDelegate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 30281d8cd5d5ed94ed89a980006f9618292a778d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945450"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate**設計工具會用來建立及設定<xref:System.Activities.Statements.InvokeDelegate>活動。

## <a name="the-invokedelegate-activity"></a>InvokeDelegate 活動

<xref:System.Activities.Statements.InvokeDelegate> 會呼叫公用委派。

### <a name="using-the-invokedelegate-activity-designer"></a>使用 InvokeDelegate 活動設計工具

**InvokeDelegate**活動設計工具可在**基本型別**類別**工具箱**，即可存取的哪一個**工具箱**  索引標籤[!INCLUDE[wfd2](../includes/wfd2-md.md)](或者，選取**工具列**從**檢視**功能表或 CRTL + ALT + X。)

**InvokeDelegate**活動設計工具可以從拖曳**工具箱**，放入[!INCLUDE[wfd2](../includes/wfd2-md.md)]介面處活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立一個 <xref:System.Activities.Statements.InvokeDelegate> 活動，具有 InvokeDelegate 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 <xref:System.Activities.Activity.DisplayName%2A>可以的標頭中編輯**InvokeDelegate**活動設計工具或**DisplayName**屬性方格的方塊。

### <a name="the-invokedelegate-properties"></a>InvokeDelegate 屬性

下表顯示 <xref:System.Activities.Statements.InvokeDelegate> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 設計工具介面上編輯。

|屬性名稱|必要|使用量|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.InvokeDelegate> 活動的易記名稱。 預設值為 InvokeDelegate。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|活動執行時要呼叫之 <xref:System.Activities.ActivityDelegate> 的名稱。 此屬性也可以在設計工具介面上編輯。 這是必要的屬性。|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|被呼叫之委派的引數集合。 金鑰是 <xref:System.Activities.DelegateArgument> 上 <xref:System.Activities.ActivityDelegate> 物件的名稱，而值是評估所屬運算式並將其指派至對應 <xref:System.Activities.DelegateArgument> 物件的引數。 在屬性方格中，按一下省略符號按鈕，在**DelegateArguments**欄位，它會顯示**DelegateArguments**對話方塊，供您設定此屬性。 按一下 **建立引數**欄位可新增引數。|

## <a name="see-also"></a>另請參閱

- [如何：在工作流程設計工具中定義及取用活動委派](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)