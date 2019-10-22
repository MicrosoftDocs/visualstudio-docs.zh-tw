---
title: TerminateWorkflow 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c204c14818a9c6e6fb0a46e6234b550838f3b1a4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607086"
---
# <a name="terminateworkflow-activity-designer"></a>TerminateWorkflow 活動設計工具
[ **TerminateWorkflow** ] 活動設計工具會用來建立和設定 <xref:System.Activities.Statements.TerminateWorkflow> 活動。

## <a name="the-terminateworkflow-activity"></a>TerminateWorkflow 活動
 <xref:System.Activities.Statements.TerminateWorkflow> 活動會終止工作流程的執行。

### <a name="using-the-terminateworkflow-activity-designer"></a>使用 TerminateWorkflow 活動設計工具
 [ **TerminateWorkflow** ] 活動設計**工具**位於 [工具箱] 的 [**運行**時間] 類別中，若要存取，請按一下 [**工具箱**] 索引標籤（也可以從 [ **View** ] 功能表選取 [**工具箱**]，或按 CTRL + ALT +X）。

 [ **TerminateWorkflow** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上通常用來放置活動的任一處，例如在 <xref:System.Activities.Statements.Sequence> 內部。 這會建立具有 TerminateWorkflow 預設**DisplayName**的 <xref:System.Activities.Statements.TerminateWorkflow> 活動。 @No__t_0 可以在 [ **TerminateWorkflow** ] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。

### <a name="the-terminateworkflow-properties"></a>TerminateWorkflow 屬性
 下表顯示 <xref:System.Activities.Statements.TerminateWorkflow> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上編輯。

|屬性名稱|必要項|使用量|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.TerminateWorkflow> 活動的易記名稱。 預設值為 TerminateWorkflow。 雖然顯示名稱並非絕對必要，但建議您盡量使用顯示名稱。|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|當工作流程終止時所要擲回的例外狀況。 請在屬性方格中設定這個屬性。|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|說明工作流程終止的原因。 請在屬性方格中設定這個屬性。|

## <a name="see-also"></a>請參閱
 [運行](../workflow-designer/runtime-activity-designers.md)時間[保存](../workflow-designer/persist-activity-designer.md)