---
title: "不支援偵錯工作流程設計工具中的案例 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
caps.latest.revision: "4"
ms.author: sdanie
manager: erikre
ms.openlocfilehash: e442c47611edbc207b3a9ba7c8f10363cd020d10
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>工作流程設計工具中不支援的偵錯情況
[!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] 中的工作流程設計工具已新增許多功能，但是依然有一些偵錯情況不受支援。 本文件詳述不支援的工作流程設計工具偵錯情況。  
  
-   在編輯程式碼之後，就無法繼續執行。  
  
-   無法從工作流程的任何一點繼續執行 (設定下一個)。  
  
-   要等到抵達游標處之後才能繼續執行 (執行至游標處)。  
  
-   工作流程設計工具無法用來偵錯以程式碼 (而不使用設計工具) 所建立的工作流程。  
  
-   以舊版 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 建立的工作流程無法在 [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] 設計工具中偵錯。  
  
-   活動或 <xref:System.Activities.Statements.Flowchart> 節點之間的連結上無法定義中斷點。  
  
-   偵錯期間不可使用剪貼簿。  
  
-   在複製或貼上活動時，不會保留中斷點。  
  
-   呼叫堆疊視窗中無法設定工作流程中斷點。  
  
-   在設計師中，建立中斷點時**列**和**字元**中的設定**新增中斷點**不使用對話方塊。  
  
-   中斷點視窗或捷徑功能表不支援以下資料行或工作流程偵錯的選項：  
  
    -   條件  
  
    -   叫用次數  
  
    -   叫用時  
  
    -   函式  
  
    -   資料  
  
    -   處理序  
  
    -   移至反組譯碼