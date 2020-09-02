---
title: DoWhile 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b63c3e2e0907bcaf13ada4cbb20ce5527a240fe3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656775"
---
# <a name="dowhile-activity-designer"></a>DoWhile 活動設計工具
<xref:System.Activities.Statements.DoWhile>活動會執行 <xref:System.Activities.Statements.DoWhile.Body%2A> 至少包含一次的活動，直到指定的條件評估為**false**為止。 如果您需要包含在迴圈主體中的活動執行零次或多次，請改用 <xref:System.Activities.Statements.While> 活動。

## <a name="dowhile-properties-in-the-workflow-designer"></a>工作流程設計工具中的 DoWhile 屬性
 下表顯示最為實用的 <xref:System.Activities.Statements.DoWhile> 活動屬性，並且說明它們在設計工具中的使用方式。

|屬性名稱|必要|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|否|條件為 **true**時要執行的活動。 若要加入 <xref:System.Activities.Statements.DoWhile.Body%2A> 活動，請從 [工具箱 **] 將** 活動拖放到 [ **DoWhile** ] 活動設計工具的 [內文] 方塊中，並在 [在此放置活動] 提示文字。|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|是|在每次迴圈重複之後所要評估的條件。 若要設定 <xref:System.Activities.Statements.DoWhile.Condition%2A> ，請在 [ [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] **DoWhile** ] 活動設計工具或屬性方格的 [**條件**] 方塊中輸入運算式。|

## <a name="see-also"></a>另請參閱
 [While](../workflow-designer/while-activity-designer.md) [控制流程](../workflow-designer/control-flow-activity-designers.md)