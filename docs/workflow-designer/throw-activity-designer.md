---
title: 工作流程設計工具擲回活動設計工具
description: 瞭解「擲回」活動，以及如何使用「擲回活動設計工具」來建立和設定「擲回」活動。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a1ffd0a9dda243e53431e419910b866853cd3932
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969095"
---
# <a name="throw-activity-designer"></a>Throw 活動設計工具

[ **Throw** ] 活動設計工具會用來建立及設定 <xref:System.Activities.Statements.Throw> 活動。

## <a name="the-throw-activity"></a>Throw 活動

<xref:System.Activities.Statements.Throw> 活動會擲回例外狀況。

### <a name="using-the-throw-activity-designer"></a>使用 Throw 活動設計工具

在 [工具箱] 的 [**錯誤處理**] 類別中存取 [**擲** 回] 活動設計 **工具**。

[ **Throw** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到工作流程設計工具介面上通常用來放置活動的任一處，例如內部 <xref:System.Activities.Statements.Sequence> 。 這會建立一個 <xref:System.Activities.Statements.Throw> 活動，其具有 Throw 的預設 **DisplayName** 。 <xref:System.Activities.Activity.DisplayName%2A>值可以在 [**擲** 回活動設計工具] 的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。 <xref:System.Activities.Statements.Throw.Exception%2A> 屬性必須在屬性方格中編輯。

### <a name="the-throw-properties"></a>擲回屬性

下表顯示 <xref:System.Activities.Statements.Throw> 屬性，並且描述屬性在設計工具中的使用方式。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|指定 <xref:System.Activities.Statements.Throw> 活動選用的易記名稱。 預設為 Throw。|
|<xref:System.Activities.Statements.Throw.Exception%2A>|是|要擲回的例外狀況。 此例外狀況必須衍生自 <xref:System.Exception>。 若要指定例外狀況，請在屬性方格中輸入 Visual Basic 運算式。|

## <a name="see-also"></a>另請參閱

- [集合](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw 活動設計工具](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
