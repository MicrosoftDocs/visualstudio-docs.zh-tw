---
title: TerminateWorkflow 活動設計工具
description: 在工作流程設計工具中，您可以瞭解如何使用 TerminateWorkflow 活動設計工具來建立和設定 TerminateWorkflow 活動。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3f37c862768dd0d72ba66d435478faed9bee8ef3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931483"
---
# <a name="terminateworkflow-activity-designer"></a>TerminateWorkflow 活動設計工具

**TerminateWorkflow** 活動設計工具是用來建立及設定 <xref:System.Activities.Statements.TerminateWorkflow> 活動。

## <a name="the-terminateworkflow-activity"></a>TerminateWorkflow 活動

<xref:System.Activities.Statements.TerminateWorkflow> 活動會終止工作流程的執行。

### <a name="using-the-terminateworkflow-activity-designer"></a>使用 TerminateWorkflow 活動設計工具

[ **TerminateWorkflow** ] 活動設計 **工具** 位於 [工具箱] 的 [**運行** 時間] 類別中，若要存取，請按一下 [**工具箱**] 索引標籤 (也可以從 [ **View** ] 功能表選取 [**工具箱**]，或按 CTRL + ALT + X。 ) 

[ **TerminateWorkflow** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到工作流程設計工具介面上通常用來放置活動的任一處，例如內部 <xref:System.Activities.Statements.Sequence> 。 這會建立一個 <xref:System.Activities.Statements.TerminateWorkflow> 活動，具有 TerminateWorkflow 的預設 **DisplayName** 。 <xref:System.Activities.Activity.DisplayName%2A>可以在 [ **TerminateWorkflow** ] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。

### <a name="the-terminateworkflow-properties"></a>TerminateWorkflow 屬性

下表顯示 <xref:System.Activities.Statements.TerminateWorkflow> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在工作流程設計工具介面上編輯。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.Activities.Statements.TerminateWorkflow> 活動的易記名稱。 預設值為 TerminateWorkflow。 雖然顯示名稱並非絕對必要，但建議您盡量使用顯示名稱。|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|否|當工作流程終止時所要擲回的例外狀況。 請在屬性方格中設定這個屬性。|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|否|說明工作流程終止的原因。 請在屬性方格中設定這個屬性。|

## <a name="see-also"></a>另請參閱

- [執行階段](../workflow-designer/runtime-activity-designers.md)
- [堅持](../workflow-designer/persist-activity-designer.md)
