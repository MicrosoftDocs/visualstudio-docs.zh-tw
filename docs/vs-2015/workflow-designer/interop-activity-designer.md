---
title: Interop 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 994d7776ff7c32f8dd309e667597550637ef2b5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659029"
---
# <a name="interop-activity-designer"></a>Interop 活動設計工具
[ **Interop** ] 活動設計工具會用來建立和設定 <xref:System.Activities.Statements.Interop> 活動。

## <a name="the-interop-activity"></a>Interop 活動
 <xref:System.Activities.Statements.Interop> 活動會管理工作流程內 <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> 所衍生型別的執行。

### <a name="using-the-interop-activity-designer"></a>使用 Interop 活動設計工具
 [ **Interop** ] 活動設計**工具**位於 [工具箱] 的 [**遷移**] 分類中，若要存取，請按一下 [**工具箱**] 索引標籤（也可以從 [**視圖**] 功能表選取 [**工具箱**]，或按 CTRL + ALT + X）。

 如果您的專案是以完整 [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] 為目標，則包含 <xref:System.Activities.Statements.Interop> 活動的 [[遷移](../workflow-designer/migration-activity-designers.md)] 分類只會顯示在 [**工具箱**] 中。

 針對C#專案，您可以用滑鼠右鍵按一下 [**方案總管**中的專案，然後選取 [**屬性**]，將專案的目標設為使用完整的 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]。 在 [**應用程式**] 索引標籤上，選取**目標 Framework**中的 [ **.net Framework 4** ] 選項。 在 [**目標 Framework 變更**] 對話方塊中選取 [**是]** 按鈕，要求您確認這項變更。

 針對 VB 專案，您可以用滑鼠右鍵按一下 [**方案總管**中的專案，然後選取 [**屬性**]，將專案的目標設為使用完整的 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]。 在 [**編譯**] 索引標籤上，按一下 [**高級編譯選項**] 按鈕。 從 [**目標 Framework] 清單**中選取 [ **.Net Framework 4** ]，然後按一下 **[確定]** 。 在 [**目標 Framework 變更**] 對話方塊中按一下 [**是]** 按鈕，要求您確認這項變更。

 [ **Interop** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上通常用來放置活動的任一處，例如在 <xref:System.Activities.Statements.Sequence> 內部。 這會建立一個 <xref:System.Activities.Statements.Interop> 活動，其中具有 Interop 的預設**DisplayName** 。 您可以在 [ **Interop** ] 活動設計工具的標頭中，或在屬性方格的 [ **DisplayName** ] 方塊中編輯 <xref:System.Activities.Activity.DisplayName%2A>。

 按一下 [**按一下以流覽 ...]** **ActivityType**方塊中的文字（在 [ **Interop** ] 活動設計工具上或在屬性方格中），以顯示 [**流覽並選取 .net 類型**] 對話方塊。 此時只會顯示工作流程 3.0 或工作流程 3.5 活動的型別 (亦即只有衍生自 <xref:System.Workflow.ComponentModel.Activity> 的型別)。 [!INCLUDE[crabout](../includes/crabout-md.md)] 使用此方塊來指定類型，請參閱[流覽和選取 .Net 類型對話方塊](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md)主題。

### <a name="the-interop-properties"></a>Interop 屬性
 下表顯示 <xref:System.Activities.Statements.Interop> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中或在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上編輯。

|屬性名稱|必要|使用量|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|偽|<xref:System.Activities.Statements.Interop> 活動的易記名稱。 預設為 Interop。 雖然顯示名稱並非絕對必要，但建議您盡量使用顯示名稱。|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|指定 <xref:System.Activities.Statements.Interop> 活動所包含之活動的活動型別。 指定的型別必須衍生自 <xref:System.Workflow.ComponentModel.Activity>。|

## <a name="see-also"></a>另請參閱
 [移轉](../workflow-designer/migration-activity-designers.md)