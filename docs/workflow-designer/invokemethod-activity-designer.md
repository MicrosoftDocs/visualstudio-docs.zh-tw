---
title: 工作流程設計工具 InvokeMethod 活動設計工具
description: 瞭解 InvokeMethod 活動，以及如何使用 InvokeMethod 活動設計工具來建立和設定 InvokeMethod 活動。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2ba7234ee0c5a4ab8096c020cb44345f17830540
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931210"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod 活動設計工具

**InvokeMethod** 設計工具是用來建立及設定 <xref:System.Activities.Statements.InvokeMethod> 活動。

## <a name="the-invokemethod-activity"></a>InvokeMethod 活動

<xref:System.Activities.Statements.InvokeMethod> 會呼叫指定物件或型別的公用方法。

### <a name="use-the-invokemethod-activity-designer"></a>使用 InvokeMethod 活動設計工具

存取 [工具箱] 的 [**基本**] 類別中的 [ **InvokeMethod** ] 活動設計 **工具**。 [ **InvokeMethod** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放在通常用來放置活動的工作流程設計工具介面上，例如內部 <xref:System.Activities.Statements.Sequence> 。 卸載活動設計工具會建立 <xref:System.Activities.Statements.InvokeMethod> 活動，預設值是 <xref:System.Activities.Activity.DisplayName%2A> InvokeMethod。 <xref:System.Activities.Activity.DisplayName%2A>可以在 [ **InvokeMethod** ] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。

### <a name="the-invokemethod-properties"></a>InvokeMethod 屬性

下表顯示這些 <xref:System.Activities.Statements.InvokeMethod> 屬性，並描述它們在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，而某些屬性可以在工作流程設計工具介面上編輯。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.Activities.Statements.InvokeMethod> 活動的易記名稱。 預設值為 InvokeMethod。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但最好是使用一個。|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|是|活動執行時要呼叫之方法的名稱。 呼叫的方法必須宣告為 **public**。 這個屬性可以在設計工具介面上編輯，而且是必要的。|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|否|要呼叫之方法的參數集合。 將參數加入至集合時，加入順序必須與參數出現在方法簽章中的順序相同。 若要顯示可以設定這個屬性的 [ **參數** ] 對話方塊，請按一下屬性方格之 [ **參數** ] 欄位中的省略號按鈕。 按一下 [ **建立引數** ] 按鈕以加入參數。|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|否|方法呼叫的傳回值。|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|是|指定是否要非同步呼叫方法。 預設值為 **[False]** 。|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|否|包含要呼叫之方法的物件。 此屬性也可以在設計工具介面上編輯。<br /><br /> 必須設定 <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 或 <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>。|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|否|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 的類型。 此屬性也可以在設計工具介面上編輯。 呼叫的方法必須是靜態的，才能設定此屬性。|

若要以 c # **out** 參數形式傳遞參數 (例如， `Method1(out myParam))` 請使用 **outargument<int>** 而非 **InOutArgument**

具有稱為 **TargetObject** 或 **Result** 的引數的方法，無法使用活動來叫用 <xref:System.Activities.Statements.InvokeMethod> 。 這是因為 <xref:System.Activities.Statements.InvokeMethod> 活動會在 <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> 中登錄 <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>、<xref:System.Activities.Statements.InvokeMethod.Result%2A> 和 <xref:System.Activities.Activity.CacheMetadata%2A>。

以下清單顯示在 <xref:System.Activities.Activity.CacheMetadata%2A> 中登錄參數的演算法：

1. 登錄 <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 引數。

2. 登錄 <xref:System.Activities.Statements.InvokeMethod.Result%2A> 引數。

3. 逐一查看 <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> 集合並登錄每個引數。

結果的例外狀況是包含以下訊息的 <xref:System.Activities.InvalidWorkflowException> 類型：'InvokeMethod'：已有名稱為 'TargetObject' 的變數、RuntimeArgument 或 DelegateArgument。 名稱在環境範圍中必須是唯一的。

此限制不適用於 <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> 和 <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> 。 它們不是工作流程引數，因此不會在 <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> 方法的活動集合中註冊 <xref:System.Activities.Statements.InvokeMethod> <xref:System.Activities.Activity.CacheMetadata%2A> 。

## <a name="see-also"></a>另請參閱

- [基本](../workflow-designer/primitives-activity-designers.md)
- [指派](../workflow-designer/assign-activity-designer.md)
- [延遲](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)
