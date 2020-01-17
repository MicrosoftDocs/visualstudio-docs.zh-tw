---
title: 工作流程設計工具重新引發活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3cb73a674e702d54f970c5dea7ec051f100382c9
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114759"
---
# <a name="rethrow-activity-designer"></a>Rethrow 活動設計工具

[**重新**擲回] 活動設計工具會用來建立和設定 <xref:System.Activities.Statements.Rethrow> 活動。

## <a name="the-rethrow-activity"></a>重新引發活動

<xref:System.Activities.Statements.Rethrow> 活動會執行先前已擲回的例外狀況。 此活動只能用於 <xref:System.Activities.Statements.Catch> 活動中的 <xref:System.Activities.Statements.TryCatch> 處理常式。

### <a name="use-the-rethrow-activity-designer"></a>使用重新引發活動設計工具

在 [工具箱] 的 [**錯誤處理**] 類別**中，存取**[重新擲回] 活動設計**工具**。 [重新**引發**] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到工作流程設計工具介面上通常用來放置活動的任一處，例如在 <xref:System.Activities.Statements.Sequence>內部。 卸載活動設計工具會建立一個 <xref:System.Activities.Statements.Rethrow> 活動，其中具有 Throw 的預設**DisplayName** 。 您可以在 [重新擲回 **] 活動設計工具的標**頭中，或在屬性方格的 [ **DisplayName** ] 方塊中編輯 <xref:System.Activities.Activity.DisplayName%2A> 值。

### <a name="the-rethrow-properties"></a>重新擲回屬性

下表顯示 <xref:System.Activities.Statements.Rethrow> 屬性，並說明它們在設計工具中的使用方式：

|內容名稱|必要|使用|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Rethrow> 活動選用的易記名稱。 預設為 Rethrow。|

## <a name="see-also"></a>請參閱

- [集合](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
