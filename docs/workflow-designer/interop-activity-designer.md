---
title: 工作流程設計工具-Interop 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 947527af9c5eb4b257f07a46b16b4d5556c48757
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55000051"
---
# <a name="interop-activity-designer"></a>Interop 活動設計工具

**Interop**活動設計工具會用來建立及設定<xref:System.Activities.Statements.Interop>活動。

## <a name="the-interop-activity"></a>Interop 活動

<xref:System.Activities.Statements.Interop> 活動會管理工作流程內 <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> 所衍生型別的執行。

### <a name="use-the-interop-activity-designer"></a>使用 Interop 活動設計工具

**Interop**活動設計工具位於**移轉**類別**工具箱**，即可存取的哪一個**工具箱** 索引標籤。或者，選取**工具箱**從**檢視**功能表，或是按下**Ctrl**+**Alt** + **X**。

[遷移](../workflow-designer/migration-activity-designers.md)包含分類<xref:System.Activities.Statements.Interop>活動只會出現在**工具箱**如果您的專案以完整的.NET Framework 4 為目標。

C# 專案，您可以將專案目標重定為使用完整的.NET Framework 4 中的專案上按一下滑鼠右鍵**方案總管**，然後選取**屬性**。 在 **應用程式**索引標籤上，選取 **.NET Framework 4**選項**目標 framework**。 選取 **是**是否確認變更。

Visual Basic 專案，您可以將專案目標重定為使用完整的.NET Framework 4 中的專案上按一下滑鼠右鍵**方案總管**，然後選取**屬性**。 在 [**編譯**索引標籤上，按一下**進階編譯選項**] 按鈕。 選取 **.Net Framework 4**從**目標 framework 清單**，然後按一下**確定**。 選取 **是**是否確認變更。

**Interop**活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面，不論活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 卸除**Interop**活動設計工具會建立<xref:System.Activities.Statements.Interop>活動，具有預設值**DisplayName**的 Interop。 您可以編輯<xref:System.Activities.Activity.DisplayName%2A>中的標頭**Interop**活動設計工具，或是在**DisplayName**屬性方格的方塊。

按一下 [**按一下即可瀏覽**中的文字**ActivityType**方塊中，在**Interop**活動設計工具上或在屬性方格中，以開啟**瀏覽和選取.Net 型別**] 對話方塊。 工作流程 3.0 或工作流程 3.5 活動的類型才會顯示。 也就是只有型別衍生自<xref:System.Workflow.ComponentModel.Activity>列示如下。 如需使用此方塊來指定類型的詳細資訊，請參閱[瀏覽並選取.NET 類型對話方塊](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md)。

### <a name="the-interop-properties"></a>Interop 屬性

下表顯示<xref:System.Activities.Statements.Interop>屬性，並描述在設計工具的使用方式。 這些屬性可以在屬性方格中或在工作流程設計工具介面上編輯。

|屬性名稱|必要項|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Interop> 活動的易記名稱。 預設值是**Interop**。 雖然顯示名稱不是必要的建議您為其提供。|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|指定 <xref:System.Activities.Statements.Interop> 活動所包含之活動的活動型別。 指定的型別必須衍生自 <xref:System.Workflow.ComponentModel.Activity>。|

## <a name="see-also"></a>另請參閱

- [移轉](../workflow-designer/migration-activity-designers.md)