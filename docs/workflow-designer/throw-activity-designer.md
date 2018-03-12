---
title: "Throw 活動設計工具 |Microsoft 文件"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e0b41fb8fcbbb80f2f99558f07c5e5a4f9e4a85b
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="throw-activity-designer"></a>Throw 活動設計工具
**擲回**活動設計工具用來建立及設定<xref:System.Activities.Statements.Throw>活動。

## <a name="the-throw-activity"></a>Throw 活動
 <xref:System.Activities.Statements.Throw> 活動會擲回例外狀況。

### <a name="using-the-throw-activity-designer"></a>使用 Throw 活動設計工具
 **擲回**活動設計工具位於**錯誤處理**分類**工具箱**，即可存取的哪一個**工具箱** 索引標籤上的左半部[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)

 **擲回**活動設計工具可以從拖曳**工具箱**，置放到上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]介面任一處活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立<xref:System.Activities.Statements.Throw>預設值的活動**DisplayName**的擲回。 <xref:System.Activities.Activity.DisplayName%2A>值可以編輯的標頭中**擲回**活動設計工具或在**DisplayName**屬性方格的方塊。 <xref:System.Activities.Statements.Throw.Exception%2A> 屬性必須在屬性方格中編輯。

### <a name="the-throw-properties"></a>擲回屬性
 下表顯示 <xref:System.Activities.Statements.Throw> 屬性，並且描述屬性在設計工具中的使用方式。

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Throw> 活動選用的易記名稱。 預設為 Throw。|
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|要擲回的例外狀況。 此例外狀況必須衍生自 <xref:System.Exception>。 若要指定例外狀況，請在屬性方格中輸入 Visual Basic 運算式。|

## <a name="see-also"></a>另請參閱

- [集合](../workflow-designer/collection-activity-designers.md)
- [重新擲回](../workflow-designer/rethrow-activity-designer.md)
- [Throw 活動設計工具](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)