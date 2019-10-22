---
title: 工作流程設計工具-InvokeDelegate
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 5227d96e3fad03dd3e3309523a6d2c68a1abdc11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650185"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate**設計工具是用來建立和設定 <xref:System.Activities.Statements.InvokeDelegate> 活動。

## <a name="the-invokedelegate-activity"></a>InvokeDelegate 活動

<xref:System.Activities.Statements.InvokeDelegate> 會呼叫公用委派。

### <a name="use-the-invokedelegate-activity-designer"></a>使用 InvokeDelegate 活動設計工具

在 [工具箱] 的 [**基本**] 類別中，存取 [ **InvokeDelegate** ] 活動設計**工具**。 [ **InvokeDelegate** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到通常用來放置活動的工作流程設計工具介面上，例如在 <xref:System.Activities.Statements.Sequence> 內部。 卸載活動設計工具會建立具有預設 <xref:System.Activities.Activity.DisplayName%2A> InvokeDelegate 的 <xref:System.Activities.Statements.InvokeDelegate> 活動。 @No__t_0 可以在 [ **InvokeDelegate** ] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。

### <a name="the-invokedelegate-properties"></a>InvokeDelegate 屬性

下表顯示 <xref:System.Activities.Statements.InvokeDelegate> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中編輯，有些則可以在工作流程設計工具介面上編輯。

|屬性名稱|必要項|使用量|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.InvokeDelegate> 活動的易記名稱。 預設值為 InvokeDelegate。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 不是絕對必要，但最好是使用其中一個。|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|活動執行時要呼叫之 <xref:System.Activities.ActivityDelegate> 的名稱。 這個屬性可以在設計工具介面上編輯，而且是必要的。|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|被呼叫之委派的引數集合。 這些索引鍵是 <xref:System.Activities.ActivityDelegate> 上參數物件的名稱，而值則是要評估運算式並將其指派給對應參數物件的引數。 若要顯示您可以設定此屬性的 [ **DelegateArguments** ] 對話方塊，請按一下屬性方格中 [ **DelegateArguments** ] 欄位的省略號按鈕。 按一下 [**建立引數**] 欄位來加入引數。|

## <a name="see-also"></a>請參閱

- [如何：定義並取用工作流程設計工具中的活動委派](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)