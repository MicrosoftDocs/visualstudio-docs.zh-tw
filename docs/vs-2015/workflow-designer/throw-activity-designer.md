---
title: Throw 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1855daa5016241fb6eb04f05d7218e02083fc0a8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655156"
---
# <a name="throw-activity-designer"></a>Throw 活動設計工具
[ **Throw** ] 活動設計工具會用來建立和設定 <xref:System.Activities.Statements.Throw> 活動。

## <a name="the-throw-activity"></a>Throw 活動
 <xref:System.Activities.Statements.Throw> 活動會擲回例外狀況。

### <a name="using-the-throw-activity-designer"></a>使用 Throw 活動設計工具
 [ **Throw** ] 活動設計工具位於 [**工具箱**] 的 [**錯誤處理**] 類別中，若要存取，請按一下 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 左邊的 [**工具箱**] 索引標籤（也可以從視圖選取 [**工具列**]）。功能表，或按 CTRL + ALT + X）。

 [ **Throw** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上通常用來放置活動的任一處，例如在 <xref:System.Activities.Statements.Sequence> 內部。 這會建立一個 <xref:System.Activities.Statements.Throw> 活動，其中具有 Throw 的預設**DisplayName** 。 您可以在 [ **Throw** ] 活動設計工具的標頭中，或在屬性方格的 [ **DisplayName** ] 方塊中編輯 <xref:System.Activities.Activity.DisplayName%2A> 值。 <xref:System.Activities.Statements.Throw.Exception%2A> 屬性必須在屬性方格中編輯。

### <a name="the-throw-properties"></a>擲回屬性
 下表顯示 <xref:System.Activities.Statements.Throw> 屬性，並且描述屬性在設計工具中的使用方式。

|屬性名稱|必要項|使用量|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Throw> 活動選用的易記名稱。 預設為 Throw。|
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|要擲回的例外狀況。 此例外狀況必須衍生自 <xref:System.Exception>。 若要指定例外狀況，請在屬性方格中輸入 Visual Basic 運算式。|

## <a name="see-also"></a>請參閱
 [集合](../workflow-designer/collection-activity-designers.md)重新[引發](../workflow-designer/rethrow-activity-designer.md)[擲回活動設計](../workflow-designer/throw-activity-designer.md)工具[TryCatch](../workflow-designer/trycatch-activity-designer.md)