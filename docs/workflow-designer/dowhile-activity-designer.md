---
title: "DoWhile 活動設計工具 |Microsoft 文件"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 76350c1a24b48e283c245180166806afe86aecd7
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="dowhile-activity-designer"></a>DoWhile 活動設計工具
<xref:System.Activities.Statements.DoWhile>活動會執行包含的活動其<xref:System.Activities.Statements.DoWhile.Body%2A>至少一次，直到指定的條件評估為**false**。 如果您需要包含在迴圈主體中的活動執行零次或多次，請改用 <xref:System.Activities.Statements.While> 活動。

## <a name="dowhile-properties-in-the-workflow-designer"></a>工作流程設計工具中的 DoWhile 屬性
 下表顯示最為實用的 <xref:System.Activities.Statements.DoWhile> 活動屬性，並且說明它們在設計工具中的使用方式。

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|要執行的條件時的活動**true**。 若要加入<xref:System.Activities.Statements.DoWhile.Body%2A>活動，請從工具箱拖曳到活動**主體**方塊**DoWhile**活動設計工具的提示文字 「 置放活動 」。|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|在每次迴圈重複之後所要評估的條件。 若要設定<xref:System.Activities.Statements.DoWhile.Condition%2A>，輸入[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]中的運算式**條件**方塊**DoWhile**活動設計工具，或在屬性方格中。|

## <a name="see-also"></a>另請參閱

- [While](../workflow-designer/while-activity-designer.md)
- [控制流程](../workflow-designer/control-flow-activity-designers.md)