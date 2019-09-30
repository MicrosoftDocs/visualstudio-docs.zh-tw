---
title: 工作流程設計工具保存活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7be70d18b1fc8ff12e2d1fb177b41775954334ed
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254853"
---
# <a name="persist-activity-designer"></a>Persist 活動設計工具

[**保存**] 活動設計工具會用來建立及<xref:System.Activities.Statements.Persist>設定活動。

## <a name="the-persist-activity"></a>Persist 活動

只要情況允許，<xref:System.Activities.Statements.Persist> 活動會將工作流程儲存至磁碟。 <xref:System.Activities.Statements.Persist> 活動無法在非持續性的區域中執行，例如在 <xref:System.Activities.Statements.TransactionScope> 活動內。 如果您在非持續<xref:System.Activities.Statements.Persist>性範圍中使用活動，則會在執行時間擲回例外狀況。

### <a name="using-the-persist-activity-designer"></a>使用 Persist 活動設計工具

[**保存**] 活動設計**工具**位於 [工具箱] 的 [**運行**時間] 類別中，若要存取，請按一下 [**工具箱**] 索引標籤（也可以從 [**視圖**] 功能表選取 [**工具箱**]，或按 CTRL + ALT + X）。

[**保存**] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到工作流程設計工具介面上通常用來放置活動的任一處<xref:System.Activities.Statements.Sequence>，例如內部。 這會建立<xref:System.Activities.Statements.Persist>一個活動，具有保存的預設**DisplayName** 。 可以<xref:System.Activities.Activity.DisplayName%2A>在 [**保存**] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。

### <a name="the-persist-properties"></a>Persist 屬性

下表顯示 <xref:System.Activities.Statements.Persist> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在工作流程設計工具介面上編輯。

|屬性名稱|必要|使用量|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Persist> 活動的易記名稱。 預設為 Persist。 雖然顯示名稱並非絕對必要，但建議您盡量使用顯示名稱。|

## <a name="see-also"></a>另請參閱

- [執行階段](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)