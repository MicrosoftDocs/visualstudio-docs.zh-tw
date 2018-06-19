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
ms.openlocfilehash: 1d441724afa1cf481bc15e2a43e6ec744a951187
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973832"
---
# <a name="rethrow-activity-designer"></a>Rethrow 活動設計工具

**重新擲回**活動設計工具用來建立及設定<xref:System.Activities.Statements.Rethrow>活動。

## <a name="the-rethrow-activity"></a>Rethrow 活動
 <xref:System.Activities.Statements.Rethrow> 活動會執行先前已擲回的例外狀況。 此活動只能用於 <xref:System.Activities.Statements.Catch> 活動中的 <xref:System.Activities.Statements.TryCatch> 處理常式。

### <a name="using-the-rethrow-activity-designer"></a>使用 ReThrow 活動設計工具
 **重新擲回**活動設計工具位於**錯誤處理**分類**工具箱**，即可存取的哪一個**工具箱** 索引標籤上的工作流程設計工具左側 (或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)

 **重新擲回**活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面上，只要活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立<xref:System.Activities.Statements.Rethrow>預設值的活動**DisplayName**的擲回。 <xref:System.Activities.Activity.DisplayName%2A>值可以編輯的標頭中**重新擲回**活動設計工具或在**DisplayName**屬性方格的方塊。

### <a name="the-rethrow-properties"></a>Rethrow 屬性
 下表顯示 <xref:System.Activities.Statements.Rethrow> 屬性，並且描述屬性在設計工具中的使用方式。

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Rethrow> 活動選用的易記名稱。 預設為 Rethrow。|

## <a name="see-also"></a>另請參閱

- [集合](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)