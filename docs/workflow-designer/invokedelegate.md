---
title: 工作流程設計工具-InvokeDelegate
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
author: TerryGLee
ms.author: tglee
ms.workload:
- multiple
ms.openlocfilehash: 9e63fb7a766b79467749cc5181a575e0d35a07b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "86876069"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate**設計工具是用來建立及設定 <xref:System.Activities.Statements.InvokeDelegate> 活動。

## <a name="the-invokedelegate-activity"></a>InvokeDelegate 活動

<xref:System.Activities.Statements.InvokeDelegate> 會呼叫公用委派。

### <a name="use-the-invokedelegate-activity-designer"></a>使用 InvokeDelegate 活動設計工具

存取 [工具箱] 的 [**基本**] 類別中的 [ **InvokeDelegate** ] 活動設計**工具**。 [ **InvokeDelegate** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放在通常用來放置活動的工作流程設計工具介面上，例如內部 <xref:System.Activities.Statements.Sequence> 。 卸載活動設計工具會建立 <xref:System.Activities.Statements.InvokeDelegate> 活動，預設值是 <xref:System.Activities.Activity.DisplayName%2A> InvokeDelegate。 <xref:System.Activities.Activity.DisplayName%2A>可以在 [ **InvokeDelegate** ] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。

### <a name="the-invokedelegate-properties"></a>InvokeDelegate 屬性

下表顯示 <xref:System.Activities.Statements.InvokeDelegate> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，而某些屬性可以在工作流程設計工具介面上編輯。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.Activities.Statements.InvokeDelegate> 活動的易記名稱。 預設值為 InvokeDelegate。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但最好是使用一個。|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|是|活動執行時要呼叫之 <xref:System.Activities.ActivityDelegate> 的名稱。 這個屬性可以在設計工具介面上編輯，而且是必要的。|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|否|被呼叫之委派的引數集合。 這些索引鍵是中的參數物件名稱 <xref:System.Activities.ActivityDelegate> ，而值則是評估運算式並將其指派給對應參數物件的引數。 若要顯示您可以設定此屬性的 [ **DelegateArguments** ] 對話方塊，請按一下屬性方格之 [ **DelegateArguments** ] 欄位中的省略號按鈕。 按一下 [ **建立引數** ] 欄位來加入引數。|

## <a name="see-also"></a>另請參閱

- [HOW TO：定義並取用工作流程設計工具中的活動委派](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)