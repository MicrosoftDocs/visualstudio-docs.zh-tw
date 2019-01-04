---
title: 工作流程設計工具-InvokeDelegate
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: fd490d15d5dc1760222446a1ae507d0e764c73f4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870530"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate**設計工具會用來建立及設定<xref:System.Activities.Statements.InvokeDelegate>活動。

## <a name="the-invokedelegate-activity"></a>InvokeDelegate 活動

<xref:System.Activities.Statements.InvokeDelegate> 會呼叫公用委派。

### <a name="use-the-invokedelegate-activity-designer"></a>使用 InvokeDelegate 活動設計工具

存取**InvokeDelegate**中的活動設計工具**基本型別**分類**工具箱**。 **InvokeDelegate**活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面，其中不斷活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 卸除活動設計工具會建立<xref:System.Activities.Statements.InvokeDelegate>預設值的活動<xref:System.Activities.Activity.DisplayName%2A>InvokeDelegate。 <xref:System.Activities.Activity.DisplayName%2A>可以的標頭中編輯**InvokeDelegate**活動設計工具或**DisplayName**屬性方格的方塊。

### <a name="the-invokedelegate-properties"></a>InvokeDelegate 屬性

下表顯示 <xref:System.Activities.Statements.InvokeDelegate> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中編輯，有些可以在工作流程設計工具介面上編輯。

|屬性名稱|必要項|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.InvokeDelegate> 活動的易記名稱。 預設值為 InvokeDelegate。<br /><br /> 雖然<xref:System.Activities.Activity.DisplayName%2A>不是絕對必要，建議您最好使用其中一個。|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|活動執行時要呼叫之 <xref:System.Activities.ActivityDelegate> 的名稱。 此屬性可編輯設計工具介面上，而且是必要的。|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|被呼叫之委派的引數集合。 索引鍵是參數物件的名稱上<xref:System.Activities.ActivityDelegate>，且值為引數的運算式會評估並指派給對應的參數物件。 若要顯示**DelegateArguments**對話方塊中，您可以設定這個屬性中，按一下省略符號按鈕，在**DelegateArguments**屬性方格的欄位。 按一下 **建立引數**欄位可新增引數。|

## <a name="see-also"></a>另請參閱

- [如何：定義和使用工作流程設計工具中的活動委派](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)