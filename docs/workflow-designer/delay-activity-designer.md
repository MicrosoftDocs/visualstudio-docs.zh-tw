---
title: 工作流程設計工具-Delay 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: abfd625a248c14f646683c7b035065e6ca096f68
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876108"
---
# <a name="delay-activity-designer"></a>Delay 活動設計工具

[ **Delay** ] 活動設計工具會用來建立及設定 <xref:System.Activities.Statements.Delay> 活動。

## <a name="the-delay-activity"></a>Delay 活動

<xref:System.Activities.Statements.Delay> 活動會延遲某個工作流程的執行，等候指定的時間長度。

### <a name="use-the-delay-activity-designer"></a>使用 Delay 活動設計工具

[ **Delay** ] 活動設計工具位於 [**工具箱**] 的 [**基本**] 類別中，若要存取，請按一下工作流程設計工具的 [**工具箱**] 索引標籤。 或者，從 [ **View** ] 功能表中選取 [**工具箱**]，或按**Ctrl** + **Alt** + **X**。

[ **Delay** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到工作流程設計工具介面上通常用來放置活動的任一處，例如內部 <xref:System.Activities.Statements.Sequence> 。 卸載活動設計工具會建立一個 <xref:System.Activities.Statements.Delay> 活動，其預設值 <xref:System.Activities.Activity.DisplayName%2A> 為 Delay。 <xref:System.Activities.Activity.DisplayName%2A>可以在 [ **Delay** ] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。

### <a name="the-delay-properties"></a>延遲屬性

下表顯示 <xref:System.Activities.Statements.Delay> 屬性，並描述它們在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在工作流程設計工具介面上編輯。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.Activities.Statements.Delay> 活動的易記名稱。 預設為 Delay。 雖然此 <xref:System.Activities.Activity.DisplayName%2A> 值不是絕對必要，但最佳作法是使用其中一個。|
|<xref:System.Activities.Statements.Delay.Duration%2A>|是|延遲工作流程的時間長度。 這個屬性會在屬性方格中設定。 輸入常值 <xref:System.TimeSpan> (使用 00:00:00 格式) 或 Visual Basic 運算式，即可指定時間長度。|

## <a name="see-also"></a>另請參閱

- [基本](../workflow-designer/primitives-activity-designers.md)
- [指派](../workflow-designer/assign-activity-designer.md)
- [Delay 活動設計工具](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)