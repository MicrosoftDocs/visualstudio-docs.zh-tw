---
title: 保存活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 60a63dd4036863641646e85a89f5018cba786802
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672618"
---
# <a name="persist-activity-designer"></a>Persist 活動設計工具
[**保存**] 活動設計工具會用來建立和設定 <xref:System.Activities.Statements.Persist> 活動。

## <a name="the-persist-activity"></a>Persist 活動
 只要情況允許，<xref:System.Activities.Statements.Persist> 活動會將工作流程儲存至磁碟。 <xref:System.Activities.Statements.Persist> 活動無法在非持續性的區域中執行，例如在 <xref:System.Activities.Statements.TransactionScope> 活動內。 如果在非持續性的範圍內使用 <xref:System.Activities.Statements.Persist> 活動，就會在執行階段擲回例外狀況。

### <a name="using-the-persist-activity-designer"></a>使用 Persist 活動設計工具
 [**保存**] 活動設計**工具**位於 [工具箱] 的 [**運行**時間] 類別中，若要存取，請按一下 [**工具箱**] 索引標籤（也可以從 [**視圖**] 功能表選取 [**工具箱**]，或按 CTRL + ALT + X）。

 [**保存**] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上通常用來放置活動的任一處，例如在 <xref:System.Activities.Statements.Sequence> 內部。 這會建立一個 <xref:System.Activities.Statements.Persist> 活動，其中預設的**DisplayName**為 [保存]。 您可以在 [**保存**] 活動設計工具的標頭中，或在屬性方格的 [ **DisplayName** ] 方塊中編輯 <xref:System.Activities.Activity.DisplayName%2A>。

### <a name="the-persist-properties"></a>Persist 屬性
 下表顯示 <xref:System.Activities.Statements.Persist> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上編輯。

|屬性名稱|必要項|使用量|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Persist> 活動的易記名稱。 預設為 Persist。 雖然顯示名稱並非絕對必要，但建議您盡量使用顯示名稱。|

## <a name="see-also"></a>請參閱
 [運行](../workflow-designer/runtime-activity-designers.md)時間[TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)