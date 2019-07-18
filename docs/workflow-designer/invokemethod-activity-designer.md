---
title: 工作流程設計工具-InvokeMethod 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eed5d81cce05b316ef7593639e868936e7f2fa69
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62537637"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod 活動設計工具

**InvokeMethod**設計工具會用來建立及設定<xref:System.Activities.Statements.InvokeMethod>活動。

## <a name="the-invokemethod-activity"></a>InvokeMethod 活動

<xref:System.Activities.Statements.InvokeMethod> 會呼叫指定物件或型別的公用方法。

### <a name="use-the-invokemethod-activity-designer"></a>使用 InvokeMethod 活動設計工具

存取**InvokeMethod**中的活動設計工具**基本型別**分類**工具箱**。 **InvokeMethod**活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面，其中不斷活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 卸除活動設計工具會建立<xref:System.Activities.Statements.InvokeMethod>預設值的活動<xref:System.Activities.Activity.DisplayName%2A>的叫用方法。 <xref:System.Activities.Activity.DisplayName%2A>可以的標頭中編輯**InvokeMethod**活動設計工具或**DisplayName**屬性方格的方塊。

### <a name="the-invokemethod-properties"></a>InvokeMethod 屬性

下表顯示<xref:System.Activities.Statements.InvokeMethod>屬性，並說明它們在設計工具的使用方式。 這些屬性可以在屬性方格中編輯，有些可以在工作流程設計工具介面上編輯。

|屬性名稱|必要|使用量|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.InvokeMethod> 活動的易記名稱。 預設值為 InvokeMethod。<br /><br /> 雖然<xref:System.Activities.Activity.DisplayName%2A>不是絕對必要，建議您最好使用其中一個。|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|活動執行時要呼叫之方法的名稱。 呼叫的方法必須宣告為**公開**。 此屬性可編輯設計工具介面上，而且是必要的。|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|要呼叫之方法的參數集合。 將參數加入至集合時，加入順序必須與參數出現在方法簽章中的順序相同。 若要顯示**參數**對話方塊中，您可以設定這個屬性中，按一下省略符號按鈕，在**參數**屬性方格的欄位。 按一下 **建立引數**按鈕以新增參數。|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|方法呼叫的傳回值。|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|指定是否要非同步呼叫方法。 預設值是 **False**。|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|包含要呼叫之方法的物件。 此屬性也可以在設計工具介面上編輯。<br /><br /> 必須設定 <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 或 <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>。|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 的類型。 此屬性也可以在設計工具介面上編輯。 呼叫的方法必須是靜態的，才能設定此屬性。|

若要將參數傳遞為 C#**放大**參數 (例如`Method1(out myParam))`，使用**OutArgument**而不是**InOutArgument**

方法呼叫的引數**TargetObject**或是**結果**無法使用叫用<xref:System.Activities.Statements.InvokeMethod>活動。 這是因為 <xref:System.Activities.Statements.InvokeMethod> 活動會在 <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> 中登錄 <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>、<xref:System.Activities.Statements.InvokeMethod.Result%2A> 和 <xref:System.Activities.Activity.CacheMetadata%2A>。

以下清單顯示在 <xref:System.Activities.Activity.CacheMetadata%2A> 中登錄參數的演算法：

1. 登錄 <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 引數。

2. 登錄 <xref:System.Activities.Statements.InvokeMethod.Result%2A> 引數。

3. 逐一查看 <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> 集合並登錄每個引數。

產生的例外狀況是型別<xref:System.Activities.InvalidWorkflowException>並出現下列訊息：' InvokeMethod':變數、 RuntimeArgument 或 DelegateArgument 已經存在名稱為 'TargetObject'。 名稱在環境範圍中必須是唯一的。

這項限制不適用於<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>和<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>。 它們不是工作流程引數，並因此未登錄在<xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>的集合<xref:System.Activities.Statements.InvokeMethod>中的活動<xref:System.Activities.Activity.CacheMetadata%2A>方法。

## <a name="see-also"></a>另請參閱

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)