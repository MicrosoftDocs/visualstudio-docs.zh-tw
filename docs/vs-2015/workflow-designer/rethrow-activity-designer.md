---
title: 重新擲回活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c65469242a60c64d6f31bfaea4fdbbf2d5251a34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663363"
---
# <a name="rethrow-activity-designer"></a>Rethrow 活動設計工具
重新擲 **回活動設計** 工具是用來建立及設定 <xref:System.Activities.Statements.Rethrow> 活動。

## <a name="the-rethrow-activity"></a>Rethrow 活動
 <xref:System.Activities.Statements.Rethrow> 活動會執行先前已擲回的例外狀況。 此活動只能用於 <xref:System.Activities.Statements.Catch> 活動中的 <xref:System.Activities.Statements.TryCatch> 處理常式。

### <a name="using-the-rethrow-activity-designer"></a>使用 ReThrow 活動設計工具
 重新擲**回活動設計工具位於 [** **工具箱**] 的 [**錯誤處理**] 類別中，若要存取，請按一下 (左側的 [**工具箱**] 索引標籤， [!INCLUDE[wfd2](../includes/wfd2-md.md)] 也可以從 [ **VIEW** ] 功能表選取 [**工具列**]，或按 CTRL + ALT + X。 ) 

 重新擲 **回活動設計** 工具可以從 [ **工具箱** ] 拖曳出來，放到介面上通常用來放置活動的任一處 [!INCLUDE[wfd2](../includes/wfd2-md.md)] ，例如內部 <xref:System.Activities.Statements.Sequence> 。 這會建立一個 <xref:System.Activities.Statements.Rethrow> 活動，其具有 Throw 的預設 **DisplayName** 。 您可以在 [重新擲回 <xref:System.Activities.Activity.DisplayName%2A> 活動設計工具**Rethrow** ] 的標頭中編輯此值，或在屬性方格的 [ **DisplayName** ] 方塊中編輯此值。

### <a name="the-rethrow-properties"></a>Rethrow 屬性
 下表顯示 <xref:System.Activities.Statements.Rethrow> 屬性，並且描述屬性在設計工具中的使用方式。

|屬性名稱|必要|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|否|指定 <xref:System.Activities.Statements.Rethrow> 活動選用的易記名稱。 預設為 Rethrow。|

## <a name="see-also"></a>另請參閱
 [集合](../workflow-designer/collection-activity-designers.md)[擲](../workflow-designer/throw-activity-designer.md)回[TryCatch](../workflow-designer/trycatch-activity-designer.md)