---
title: "Interop 活動設計工具 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 726bc2fa995d819b0e554e11439c85f9fdf19243
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="interop-activity-designer"></a>Interop 活動設計工具
**Interop**活動設計工具用來建立及設定<xref:System.Activities.Statements.Interop>活動。  
  
## <a name="the-interop-activity"></a>Interop 活動  
 <xref:System.Activities.Statements.Interop> 活動會管理工作流程內 <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> 所衍生型別的執行。  
  
### <a name="using-the-interop-activity-designer"></a>使用 Interop 活動設計工具  
 **Interop**活動設計工具位於**移轉**分類**工具箱**，即可存取的哪一個**工具箱** 索引標籤 (或者，選取**工具箱**從**檢視**功能表或 CTRL + ALT + X。)  
  
 [移轉](../workflow-designer/migration-activity-designers.md)包含分類<xref:System.Activities.Statements.Interop>活動只會出現在**工具箱**如果您專案的目標完整[!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)]。  
  
 針對 C# 專案，您可以重新擬定專案目標，使用完整[!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)]中的專案上按一下滑鼠右鍵**方案總管 中**，然後選取**屬性**。 在**應用程式**索引標籤上，選取**NET Framework 4**選項**目標 framework**。 選取**是**按鈕**目標 Framework 變更**對話方塊，顯示詢問您是否確認這項變更。  
  
 對於 VB 專案，您可以重新擬定專案目標，使用完整[!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)]中的專案上按一下滑鼠右鍵**方案總管 中**，然後選取**屬性**。 在**編譯**索引標籤上，按一下 [**進階編譯選項**] 按鈕。 選取**.Net Framework 4**從**目標 framework 清單**，然後按一下 **確定**。 按一下**是**按鈕**目標 Framework 變更**對話方塊，顯示詢問您是否確認這項變更。  
  
 **Interop**活動設計工具可以從拖曳**工具箱**，置放到上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]介面任一處活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立<xref:System.Activities.Statements.Interop>預設值的活動**DisplayName**的 Interop。 <xref:System.Activities.Activity.DisplayName%2A>可編輯的標頭中**Interop**活動設計工具或在**DisplayName**屬性方格的方塊。  
  
 按一下**按一下即可瀏覽...**中的文字**ActivityType**方塊上**Interop**活動設計工具，或在屬性方格中，以顯示**瀏覽並選取.Net 型別**對話方塊。 此時只會顯示工作流程 3.0 或工作流程 3.5 活動的型別 (亦即只有衍生自 <xref:System.Workflow.ComponentModel.Activity> 的型別)。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]使用此方塊以指定的類型，請參閱[瀏覽並選取.NET 類型對話方塊](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md)主題。  
  
### <a name="the-interop-properties"></a>Interop 屬性  
 下表顯示 <xref:System.Activities.Statements.Interop> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中或在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上編輯。  
  
|屬性名稱|必要項|使用方式|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Interop> 活動的易記名稱。 預設為 Interop。 雖然顯示名稱並非絕對必要，但建議您盡量使用顯示名稱。|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|指定 <xref:System.Activities.Statements.Interop> 活動所包含之活動的活動型別。 指定的型別必須衍生自 <xref:System.Workflow.ComponentModel.Activity>。|  
  
## <a name="see-also"></a>請參閱  
 [移轉](../workflow-designer/migration-activity-designers.md)