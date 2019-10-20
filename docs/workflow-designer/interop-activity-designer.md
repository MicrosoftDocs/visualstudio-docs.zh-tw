---
title: 工作流程設計工具-Interop 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8047df3787c0871e369b6079e4f0cc80f6d93949
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650215"
---
# <a name="interop-activity-designer"></a>Interop 活動設計工具

[ **Interop** ] 活動設計工具會用來建立和設定 <xref:System.Activities.Statements.Interop> 活動。

## <a name="the-interop-activity"></a>Interop 活動

<xref:System.Activities.Statements.Interop> 活動會管理工作流程內 <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> 所衍生型別的執行。

### <a name="use-the-interop-activity-designer"></a>使用 Interop 活動設計工具

[ **Interop** ] 活動設計**工具**位於 [工具箱] 的 [**遷移**] 分類中，按一下 [**工具箱**] 索引標籤即可存取。或者，從 [ **View** ] 功能表選取 [**工具箱**]，或按**Ctrl**+**Alt** +**X**。

如果您的專案是以 .NET Framework 4 （完整）或更新版本為目標，則包含 <xref:System.Activities.Statements.Interop> 活動的 [[遷移](../workflow-designer/migration-activity-designers.md)] 分類只會出現在 [**工具箱**] 中。 如有需要，您可以變更專案的目標 framework 版本。

[ **Interop** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到工作流程設計工具介面上通常用來放置活動的任一處，例如在 <xref:System.Activities.Statements.Sequence> 內部。 卸載 [ **interop** ] 活動設計工具會建立一個 <xref:System.Activities.Statements.Interop> 活動，其中具有 Interop 的預設**DisplayName** 。 您可以在 [ **Interop** ] 活動設計工具的標頭中，或在屬性方格的 [ **DisplayName** ] 方塊中編輯 <xref:System.Activities.Activity.DisplayName%2A>。

在 [ **Interop** ] 活動設計工具上或在屬性方格中，按一下 [ **ActivityType** ] 方塊中的 [**按一下以流覽**文字]，開啟 [**流覽並選取 .net 類型**] 對話方塊。 只會顯示工作流程3.0 或工作流程3.5 活動的類型。 也就是說，只會顯示衍生自 <xref:System.Workflow.ComponentModel.Activity> 的類型。 如需使用此方塊來指定類型的詳細資訊，請參閱[流覽並選取 .Net 類型對話方塊](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md)。

### <a name="the-interop-properties"></a>Interop 屬性

下表顯示 <xref:System.Activities.Statements.Interop> 屬性，並說明如何在設計工具中使用它們。 這些屬性可以在屬性方格中或在工作流程設計工具介面上編輯。

|屬性名稱|必要項|使用量|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Interop> 活動的易記名稱。 預設值為**Interop**。 雖然不需要顯示名稱，但建議提供一個。|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|指定 <xref:System.Activities.Statements.Interop> 活動所包含之活動的活動型別。 指定的型別必須衍生自 <xref:System.Workflow.ComponentModel.Activity>。|

## <a name="see-also"></a>請參閱

- [移轉](../workflow-designer/migration-activity-designers.md)