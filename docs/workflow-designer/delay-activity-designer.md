---
title: 工作流程設計工具-Delay 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c793456cd32d6d5749bcda8c8d266f6cd939601
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823658"
---
# <a name="delay-activity-designer"></a>Delay 活動設計工具

**延遲**活動設計工具會用來建立及設定<xref:System.Activities.Statements.Delay>活動。

## <a name="the-delay-activity"></a>Delay 活動

<xref:System.Activities.Statements.Delay> 活動會延遲某個工作流程的執行，等候指定的時間長度。

### <a name="use-the-delay-activity-designer"></a>使用 Delay 活動設計工具

**延遲**活動設計工具可在**基本型別**分類**工具箱**，即可存取的哪一個**工具箱**工作流程設計工具 索引標籤。 或者，選取**工具箱**從**檢視**功能表，或是按下**Ctrl**+**Alt** + **X**。

**延遲**活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面，不論活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 卸除活動設計工具會建立<xref:System.Activities.Statements.Delay>預設值的活動<xref:System.Activities.Activity.DisplayName%2A>的延遲。 <xref:System.Activities.Activity.DisplayName%2A>可以的標頭中編輯**延遲**活動設計工具或**DisplayName**屬性方格的方塊。

### <a name="the-delay-properties"></a>Delay 屬性

下表顯示<xref:System.Activities.Statements.Delay>屬性，並說明它們在設計工具的使用方式。 這些屬性可以在屬性方格中編輯，其中一些可以在工作流程設計工具介面上編輯。

|屬性名稱|必要項|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Delay> 活動的易記名稱。 預設為 Delay。 雖然<xref:System.Activities.Activity.DisplayName%2A>值不是絕對必要，是最佳的做法是使用其中一個。|
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|延遲工作流程的時間長度。 這個屬性會在屬性方格中設定。 輸入常值 <xref:System.TimeSpan> (使用 00:00:00 格式) 或 Visual Basic 運算式，即可指定時間長度。|

## <a name="see-also"></a>另請參閱

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay 活動設計工具](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)