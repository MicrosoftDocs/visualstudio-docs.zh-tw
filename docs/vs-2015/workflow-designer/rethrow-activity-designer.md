---
title: Rethrow 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8b023a42da1c862927606c4bec0215120a5e5a11
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62937753"
---
# <a name="rethrow-activity-designer"></a>Rethrow 活動設計工具
**重新擲回**活動設計工具會用來建立及設定<xref:System.Activities.Statements.Rethrow>活動。  
  
## <a name="the-rethrow-activity"></a>Rethrow 活動  
 <xref:System.Activities.Statements.Rethrow> 活動會執行先前已擲回的例外狀況。 此活動只能用於 <xref:System.Activities.Statements.Catch> 活動中的 <xref:System.Activities.Statements.TryCatch> 處理常式。  
  
### <a name="using-the-rethrow-activity-designer"></a>使用 ReThrow 活動設計工具  
 **重新擲回**活動設計工具位於**錯誤處理**類別**工具箱**，即可存取的哪一個**工具箱** 索引標籤上的左側[!INCLUDE[wfd2](../includes/wfd2-md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)  
  
 **重新擲回**活動設計工具可以從拖曳**工具箱**，放入[!INCLUDE[wfd2](../includes/wfd2-md.md)]介面只要活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立<xref:System.Activities.Statements.Rethrow>活動，具有預設值**DisplayName**的擲回。 <xref:System.Activities.Activity.DisplayName%2A>可以編輯的標頭中的值**重新擲回**活動設計工具或**DisplayName**屬性方格的方塊。  
  
### <a name="the-rethrow-properties"></a>Rethrow 屬性  
 下表顯示 <xref:System.Activities.Statements.Rethrow> 屬性，並且描述屬性在設計工具中的使用方式。  
  
|屬性名稱|必要|使用量|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Rethrow> 活動選用的易記名稱。 預設為 Rethrow。|  
  
## <a name="see-also"></a>另請參閱  
 [集合](../workflow-designer/collection-activity-designers.md)   
 [擲回](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)