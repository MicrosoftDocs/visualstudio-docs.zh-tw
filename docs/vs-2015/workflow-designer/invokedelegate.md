---
title: InvokeDelegate |Microsoft Docs
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
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc35aec714255b467431488936605fb37009db9d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659010"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate**設計工具是用來建立及設定 <xref:System.Activities.Statements.InvokeDelegate> 活動。

## <a name="the-invokedelegate-activity"></a>InvokeDelegate 活動

<xref:System.Activities.Statements.InvokeDelegate> 會呼叫公用委派。

### <a name="using-the-invokedelegate-activity-designer"></a>使用 InvokeDelegate 活動設計工具

[ **InvokeDelegate** ] 活動設計工具位於 [**工具箱**] 的 [**基本**] 類別中，若要存取，請按一下 [**工具箱**] 索引標籤 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (或者，從 [ **View** ] 功能表選取 [**工具列**]，或 CRTL + ALT + X. ) 

[ **InvokeDelegate** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到介面上通常用來 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 放置活動的位置，例如內部 <xref:System.Activities.Statements.Sequence> 。 這會建立一個 <xref:System.Activities.Statements.InvokeDelegate> 活動，具有 InvokeDelegate 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 <xref:System.Activities.Activity.DisplayName%2A>可以在 [ **InvokeDelegate** ] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。

### <a name="the-invokedelegate-properties"></a>InvokeDelegate 屬性

下表顯示 <xref:System.Activities.Statements.InvokeDelegate> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 設計工具介面上編輯。

|屬性名稱|必要|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.Activities.Statements.InvokeDelegate> 活動的易記名稱。 預設值為 InvokeDelegate。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|是|活動執行時要呼叫之 <xref:System.Activities.ActivityDelegate> 的名稱。 此屬性也可以在設計工具介面上編輯。 這是必要的屬性。|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|否|被呼叫之委派的引數集合。 金鑰是 <xref:System.Activities.DelegateArgument> 上 <xref:System.Activities.ActivityDelegate> 物件的名稱，而值是評估所屬運算式並將其指派至對應 <xref:System.Activities.DelegateArgument> 物件的引數。 在屬性方格中，按一下 [ **DelegateArguments** ] 欄位中的省略號按鈕，就會顯示 [ **DelegateArguments** ] 對話方塊，讓您設定這個屬性。 按一下 [ **建立引數** ] 欄位來加入引數。|

## <a name="see-also"></a>另請參閱

- [HOW TO：定義並取用工作流程設計工具中的活動委派](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)