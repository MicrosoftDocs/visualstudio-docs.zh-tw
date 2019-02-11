---
title: 工作流程設計工具-Throw 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7074ee2a11759983f103024033cb2b96322330cc
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55935871"
---
# <a name="throw-activity-designer"></a>Throw 活動設計工具

**擲回**活動設計工具會用來建立及設定<xref:System.Activities.Statements.Throw>活動。

## <a name="the-throw-activity"></a>Throw 活動

<xref:System.Activities.Statements.Throw> 活動會擲回例外狀況。

### <a name="using-the-throw-activity-designer"></a>使用 Throw 活動設計工具

存取權**擲回**中的活動設計工具**錯誤處理**類別**工具箱**。

**擲回**活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面，不論活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立<xref:System.Activities.Statements.Throw>活動，具有預設值**DisplayName**的擲回。 <xref:System.Activities.Activity.DisplayName%2A>可以編輯的標頭中的值**擲回**活動設計工具或**DisplayName**屬性方格的方塊。 <xref:System.Activities.Statements.Throw.Exception%2A> 屬性必須在屬性方格中編輯。

### <a name="the-throw-properties"></a>擲回屬性

下表顯示 <xref:System.Activities.Statements.Throw> 屬性，並且描述屬性在設計工具中的使用方式。

|屬性名稱|必要項|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Throw> 活動選用的易記名稱。 預設為 Throw。|
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|要擲回的例外狀況。 此例外狀況必須衍生自 <xref:System.Exception>。 若要指定例外狀況，請在屬性方格中輸入 Visual Basic 運算式。|

## <a name="see-also"></a>另請參閱

- [集合](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw 活動設計工具](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)