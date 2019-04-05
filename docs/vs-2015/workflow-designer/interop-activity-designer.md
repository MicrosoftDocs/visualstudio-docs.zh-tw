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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 55829e85b17bcdc70e419a8496d4756d0acb4a56
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940755"
---
# <a name="interop-activity-designer"></a>Interop 活動設計工具
**Interop**活動設計工具會用來建立及設定<xref:System.Activities.Statements.Interop>活動。  
  
## <a name="the-interop-activity"></a>Interop 活動  
 <xref:System.Activities.Statements.Interop> 活動會管理工作流程內 <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> 所衍生型別的執行。  
  
### <a name="using-the-interop-activity-designer"></a>使用 Interop 活動設計工具  
 **Interop**活動設計工具位於**移轉**類別**工具箱**，即可存取的哪一個**工具箱** 索引標籤 (或者，選取**工具箱**從**檢視**功能表或 CTRL + ALT + X。)  
  
 [遷移](../workflow-designer/migration-activity-designers.md)包含分類<xref:System.Activities.Statements.Interop>活動只會出現在**工具箱**如果您的專案針對完整[!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)]。  
  
 C# 專案，您可以重新擬定專案目標，使用完整[!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]中的專案上按一下滑鼠右鍵**方案總管**，然後選取**屬性**。 在 **應用程式**索引標籤上，選取 **.NET Framework 4**選項**目標 framework**。 選取  **是**按鈕**目標 Framework 變更**顯示詢問您是否確認這項變更的對話方塊。  
  
 對於 VB 專案，您可以重新擬定專案目標，使用完整[!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]中的專案上按一下滑鼠右鍵**方案總管**，然後選取**屬性**。 在 [**編譯**索引標籤上，按一下**進階編譯選項**] 按鈕。 選取  **.Net Framework 4**從**目標 framework 清單**，然後按一下 **確定**。 按一下  **是**按鈕**目標 Framework 變更**顯示詢問您是否確認這項變更的對話方塊。  
  
 **Interop**活動設計工具可以從拖曳**工具箱**，放入[!INCLUDE[wfd2](../includes/wfd2-md.md)]介面只要活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立<xref:System.Activities.Statements.Interop>活動，具有預設值**DisplayName**的 Interop。 <xref:System.Activities.Activity.DisplayName%2A>可以的標頭中編輯**Interop**活動設計工具或**DisplayName**屬性方格的方塊。  
  
 按一下 **按一下即可瀏覽...** 中的文字**ActivityType**方塊中，依據**Interop**活動設計工具上或在屬性方格中，以顯示**瀏覽並選取.Net 型別** 對話方塊。 此時只會顯示工作流程 3.0 或工作流程 3.5 活動的型別 (亦即只有衍生自 <xref:System.Workflow.ComponentModel.Activity> 的型別)。 [!INCLUDE[crabout](../includes/crabout-md.md)] 使用此方塊來指定類型，請參閱[瀏覽並選取.NET 類型對話方塊](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md)主題。  
  
### <a name="the-interop-properties"></a>Interop 屬性  
 下表顯示 <xref:System.Activities.Statements.Interop> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中或在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上編輯。  
  
|屬性名稱|必要|使用量|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Interop> 活動的易記名稱。 預設為 Interop。 雖然顯示名稱並非絕對必要，但建議您盡量使用顯示名稱。|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|指定 <xref:System.Activities.Statements.Interop> 活動所包含之活動的活動型別。 指定的型別必須衍生自 <xref:System.Workflow.ComponentModel.Activity>。|  
  
## <a name="see-also"></a>另請參閱  
 [移轉](../workflow-designer/migration-activity-designers.md)