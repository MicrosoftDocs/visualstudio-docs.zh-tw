---
title: 工作流程設計工具-Rethrow 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 24c13b629047b73b3f3ee15f2fc25a0120a2c177
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755251"
---
# <a name="rethrow-activity-designer"></a>Rethrow 活動設計工具

**重新擲回**活動設計工具會用來建立及設定<xref:System.Activities.Statements.Rethrow>活動。

## <a name="the-rethrow-activity"></a>Rethrow 活動

<xref:System.Activities.Statements.Rethrow> 活動會執行先前已擲回的例外狀況。 此活動只能用於 <xref:System.Activities.Statements.Catch> 活動中的 <xref:System.Activities.Statements.TryCatch> 處理常式。

### <a name="use-the-rethrow-activity-designer"></a>使用 ReThrow 活動設計工具

存取權**重新擲回**中的活動設計工具**錯誤處理**類別**工具箱**。 **重新擲回**活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面，不論活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 卸除活動設計工具會建立<xref:System.Activities.Statements.Rethrow>活動，具有預設值**DisplayName**的擲回。 <xref:System.Activities.Activity.DisplayName%2A>可以編輯的標頭中的值**重新擲回**活動設計工具，或是在**DisplayName**屬性方格的方塊。

### <a name="the-rethrow-properties"></a>Rethrow 屬性

下表顯示<xref:System.Activities.Statements.Rethrow>屬性，並說明它們在設計工具的使用方式：

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Rethrow> 活動選用的易記名稱。 預設為 Rethrow。|

## <a name="see-also"></a>另請參閱

- [集合](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)