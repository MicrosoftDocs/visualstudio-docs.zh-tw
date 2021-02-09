---
title: 工作流程設計工具-Interop 活動設計工具
description: 瞭解 Interop 活動設計工具，以及如何使用 Interop 活動設計工具來建立和設定 Interop 活動。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: jillre
ms.author: jillfra
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: edf4658743bb719c1c23f93b2d1d3cc33afdbaba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847384"
---
# <a name="interop-activity-designer"></a>Interop 活動設計工具

[ **Interop** ] 活動設計工具會用來建立及設定 <xref:System.Activities.Statements.Interop> 活動。

## <a name="the-interop-activity"></a>Interop 活動

<xref:System.Activities.Statements.Interop> 活動會管理工作流程內 <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> 所衍生型別的執行。

### <a name="use-the-interop-activity-designer"></a>使用 Interop 活動設計工具

[ **Interop** ] 活動設計工具位於 [**工具箱**] 的 [**遷移**] 類別中，若要存取，請按一下 [**工具箱**] 索引標籤。或者，從 [ **View** ] 功能表選取 [**工具箱**]，或按 **Ctrl** + **Alt** + **X**。

[](../workflow-designer/migration-activity-designers.md) <xref:System.Activities.Statements.Interop> 如果您的專案以 .NET Framework 4 (full) 或更新版本為目標，則包含活動的遷移類別只會出現在 [**工具箱**] 中。 如有必要，您可以變更專案的目標 framework 版本。

[ **Interop** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到工作流程設計工具介面上通常用來放置活動的任一處，例如內部 <xref:System.Activities.Statements.Sequence> 。 卸載 **interop** 活動設計工具 <xref:System.Activities.Statements.Interop> 時，會建立具有 Interop 預設 **DisplayName** 的活動。 您可以在 [ <xref:System.Activities.Activity.DisplayName%2A> **Interop** ] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。

在 [ **Interop** ] 活動設計工具上或在屬性方格中，按一下 [ **ActivityType** ] 方塊中的 [**按一下以流覽** 文字]，以開啟 [**流覽並選取 .net 類型**] 對話方塊。 只會顯示工作流程3.0 或工作流程3.5 活動的類型。 也就是說，只會顯示衍生自的類型 <xref:System.Workflow.ComponentModel.Activity> 。 如需使用這個方塊來指定類型的詳細資訊，請參閱 [流覽並選取 .Net 類型對話方塊](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md)。

### <a name="the-interop-properties"></a>Interop 屬性

下表顯示 <xref:System.Activities.Statements.Interop> 屬性，並描述如何在設計工具中使用它們。 這些屬性可以在屬性方格中或在工作流程設計工具介面上編輯。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.Activities.Statements.Interop> 活動的易記名稱。 預設值為 **Interop**。 雖然顯示名稱不是必要的，但建議您提供。|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|是|指定 <xref:System.Activities.Statements.Interop> 活動所包含之活動的活動型別。 指定的型別必須衍生自 <xref:System.Workflow.ComponentModel.Activity>。|

## <a name="see-also"></a>另請參閱

- [移轉](../workflow-designer/migration-activity-designers.md)