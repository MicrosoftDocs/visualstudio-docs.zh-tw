---
title: 工作流程設計工具 DoWhile 活動設計工具
description: 瞭解 DoWhile 活動如何執行其主體中包含的活動至少一次，直到指定的條件評估為 false 為止。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6e117fcbea0488c4b6a42125971984b86cf78251
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894253"
---
# <a name="dowhile-activity-designer"></a>DoWhile 活動設計工具

<xref:System.Activities.Statements.DoWhile>活動會執行 <xref:System.Activities.Statements.DoWhile.Body%2A> 至少包含一次的活動，直到指定的條件評估為 **false** 為止。 如果您需要包含在迴圈主體中的活動執行零次或多次，請改用 <xref:System.Activities.Statements.While> 活動。

## <a name="dowhile-properties-in-the-workflow-designer"></a>工作流程設計工具中的 DoWhile 屬性

下表顯示最有用的 <xref:System.Activities.Statements.DoWhile> 活動屬性，並說明如何在設計工具中使用它們：

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|否|條件為 **true** 時要執行的活動。 若要加入 <xref:System.Activities.Statements.DoWhile.Body%2A> 活動，請從 [工具箱 **] 將** 活動拖放到 [ **DoWhile** ] 活動設計工具的 [內文] 方塊中，並在 [在此放置活動] 提示文字。|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|是|在每次迴圈重複之後所要評估的條件。 若要設定 <xref:System.Activities.Statements.DoWhile.Condition%2A> ，請在 [ **DoWhile** ] 活動設計工具的 [**條件**] 方塊或在屬性方格中輸入 Visual Basic 運算式。|

## <a name="see-also"></a>另請參閱

- [While](../workflow-designer/while-activity-designer.md)
- [控制流程](../workflow-designer/control-flow-activity-designers.md)