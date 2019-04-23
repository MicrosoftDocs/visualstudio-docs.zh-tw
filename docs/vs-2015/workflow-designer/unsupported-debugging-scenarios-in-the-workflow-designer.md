---
title: 不支援偵錯工作流程設計工具中的案例 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
caps.latest.revision: 4
author: steved0x
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7b3b47264190afcc75431a55ad6b8b4512f26ea0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082683"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>工作流程設計工具中不支援的偵錯情況
[!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 中的工作流程設計工具已新增許多功能，但是依然有一些偵錯情況不受支援。 本文件詳述不支援的工作流程設計工具偵錯情況。  
  
- 在編輯程式碼之後，就無法繼續執行。  
  
- 無法從工作流程的任何一點繼續執行 (設定下一個)。  
  
- 要等到抵達游標處之後才能繼續執行 (執行至游標處)。  
  
- 工作流程設計工具無法用來偵錯以程式碼 (而不使用設計工具) 所建立的工作流程。  
  
- 以舊版 [!INCLUDE[wf](../includes/wf-md.md)] 建立的工作流程無法在 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 設計工具中偵錯。  
  
- 活動或 <xref:System.Activities.Statements.Flowchart> 節點之間的連結上無法定義中斷點。  
  
- 偵錯期間不可使用剪貼簿。  
  
- 在複製或貼上活動時，不會保留中斷點。  
  
- 呼叫堆疊視窗中無法設定工作流程中斷點。  
  
- 在設計師中，建立中斷點時**線條**並**字元**中的設定**新中斷點**對話方塊不會使用。  
  
- 中斷點視窗或捷徑功能表不支援以下資料行或工作流程偵錯的選項：  
  
    - 條件  
  
    - 叫用次數  
  
    - 叫用時  
  
    - 功能  
  
    - 資料  
  
    - 處理序  
  
    - 移至反組譯碼