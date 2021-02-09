---
title: 工作流程設計工具重新擲回活動設計工具
description: 瞭解重新擲回活動，以及如何使用重新擲回活動設計工具來建立和設定重新擲回活動。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2e3615c73583e8c5c313d23fd5f9aa6d9fcd5ff4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847319"
---
# <a name="rethrow-activity-designer"></a>Rethrow 活動設計工具

重新擲 **回活動設計** 工具是用來建立及設定 <xref:System.Activities.Statements.Rethrow> 活動。

## <a name="the-rethrow-activity"></a>重新擲回活動

<xref:System.Activities.Statements.Rethrow> 活動會執行先前已擲回的例外狀況。 此活動只能用於 <xref:System.Activities.Statements.Catch> 活動中的 <xref:System.Activities.Statements.TryCatch> 處理常式。

### <a name="use-the-rethrow-activity-designer"></a>使用重新擲回活動設計工具

存取 [工具箱] 的 [**錯誤處理**] 類別中的 [重新擲 **回活動設計****工具**]。 重新擲回活動設計工具可以從 [**工具箱**] 拖曳出來，放到工作流程設計工具介面上通常用來放置 **活動的任一** 處，例如內部 <xref:System.Activities.Statements.Sequence> 。 卸載活動設計工具時，會建立一個 <xref:System.Activities.Statements.Rethrow> 具有 Throw 預設 **DisplayName** 的活動。 值可以在 [重新擲回 <xref:System.Activities.Activity.DisplayName%2A> 活動設計工具 ] 的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。

### <a name="the-rethrow-properties"></a>重新擲回屬性

下表顯示 <xref:System.Activities.Statements.Rethrow> 屬性，並描述如何在設計工具中使用這些屬性：

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|指定 <xref:System.Activities.Statements.Rethrow> 活動選用的易記名稱。 預設為 Rethrow。|

## <a name="see-also"></a>另請參閱

- [集合](../workflow-designer/collection-activity-designers.md)
- [扔](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
