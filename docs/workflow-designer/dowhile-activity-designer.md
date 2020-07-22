---
title: 工作流程設計工具 DoWhile 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c56a9ab8b46f8f7ee36875dda507cb9f288136cf
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86875601"
---
# <a name="dowhile-activity-designer"></a>DoWhile 活動設計工具

<xref:System.Activities.Statements.DoWhile>活動會執行 <xref:System.Activities.Statements.DoWhile.Body%2A> 至少包含一次的活動，直到指定的條件評估為**false**為止。 如果您需要包含在迴圈主體中的活動執行零次或多次，請改用 <xref:System.Activities.Statements.While> 活動。

## <a name="dowhile-properties-in-the-workflow-designer"></a>工作流程設計工具中的 DoWhile 屬性

下表顯示最有用的 <xref:System.Activities.Statements.DoWhile> 活動屬性，並說明如何在設計工具中使用它們：

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|否|條件為**true**時要執行的活動。 若要新增 <xref:System.Activities.Statements.DoWhile.Body%2A> 活動，請將活動從 [工具箱] 拖**Body**放到 [ **DoWhile** ] 活動設計工具上的 [內文] 方塊中，並出現提示文字「在此放置活動」。|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|是|在每次迴圈重複之後所要評估的條件。 若要設定 <xref:System.Activities.Statements.DoWhile.Condition%2A> ，請在 [ **DoWhile** ] 活動設計工具上或在屬性方格的 [**條件**] 方塊中輸入 Visual Basic 運算式。|

## <a name="see-also"></a>另請參閱

- [While](../workflow-designer/while-activity-designer.md)
- [控制流程](../workflow-designer/control-flow-activity-designers.md)