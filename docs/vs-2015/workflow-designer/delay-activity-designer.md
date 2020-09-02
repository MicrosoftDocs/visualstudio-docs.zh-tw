---
title: Delay 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a47279bc68503ba645fea3ef23a04ce9d5ef4c41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656804"
---
# <a name="delay-activity-designer"></a>Delay 活動設計工具
**Delay**活動設計工具是用來建立及設定 <xref:System.Activities.Statements.Delay> 活動。

## <a name="the-delay-activity"></a>Delay 活動
 <xref:System.Activities.Statements.Delay> 活動會延遲某個工作流程的執行，等候指定的時間長度。

### <a name="using-the-delay-activity-designer"></a>使用 Delay 活動設計工具
 [**延遲**] 活動設計工具位於 [**工具箱**] 的 [**基本**] 類別中，若要存取，請按一下 (的 [**工具箱**] 索引標籤，也可以 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 從 [ **VIEW** ] 功能表選取 [**工具列**]，或按 CTRL + ALT + X。 ) 

 [ **延遲** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到介面上通常用來放置活動的任一處 [!INCLUDE[wfd2](../includes/wfd2-md.md)] ，例如內部 <xref:System.Activities.Statements.Sequence> 。 這會建立一個 <xref:System.Activities.Statements.Delay> 活動，具有 Delay 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 <xref:System.Activities.Activity.DisplayName%2A>可以在 [**延遲**] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。

### <a name="the-delay-properties"></a>Delay 屬性
 下表顯示 <xref:System.Activities.Statements.Delay> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 設計工具介面上編輯。

|屬性名稱|必要|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.Activities.Statements.Delay> 活動的易記名稱。 預設為 Delay。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.Delay.Duration%2A>|是|延遲工作流程的時間長度。 這個屬性會在屬性方格中設定。 輸入常值 <xref:System.TimeSpan> (使用 00:00:00 格式) 或 Visual Basic 運算式，即可指定時間長度。|

## <a name="see-also"></a>另請參閱
 [基本](../workflow-designer/primitives-activity-designers.md)[指派](../workflow-designer/assign-activity-designer.md)[延遲活動設計](../workflow-designer/delay-activity-designer.md)工具[InvokeMethod](../workflow-designer/invokemethod-activity-designer.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)