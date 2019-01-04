---
title: 工作流程設計工具-DoWhile 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc96d44a38a0cf8a1865de236b9f7ef473c960a7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53960426"
---
# <a name="dowhile-activity-designer"></a>DoWhile 活動設計工具

<xref:System.Activities.Statements.DoWhile>活動會在執行中包含的活動及其<xref:System.Activities.Statements.DoWhile.Body%2A>至少一次，直到指定的條件評估為為止**false**。 如果您需要包含在迴圈主體中的活動執行零次或多次，請改用 <xref:System.Activities.Statements.While> 活動。

## <a name="dowhile-properties-in-the-workflow-designer"></a>工作流程設計工具中的 DoWhile 屬性

下表顯示最為實用<xref:System.Activities.Statements.DoWhile>活動屬性，並說明如何在設計工具中使用它們：

|屬性名稱|必要項|使用方式|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|要執行的條件時的活動 **，則為 true**。 若要新增<xref:System.Activities.Statements.DoWhile.Body%2A>活動，請從工具箱拖曳到**主體**方塊**DoWhile**活動設計工具提示文字 「 置放活動 」 與。|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|在每次迴圈重複之後所要評估的條件。 若要設定<xref:System.Activities.Statements.DoWhile.Condition%2A>，輸入在 Visual Basic 運算式**條件**方塊**DoWhile**活動設計工具上或在屬性方格中。|

## <a name="see-also"></a>另請參閱

- [While](../workflow-designer/while-activity-designer.md)
- [控制流程](../workflow-designer/control-flow-activity-designers.md)