---
title: 工作流程設計工具中不支援的偵錯情況
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 83c9b1158319b580bc860982b6c51c9c28edf5af
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433873"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>工作流程設計工具中不支援的偵錯情況

在.NET Framework 4 工作流程設計工具加入許多新功能，但仍有某些不支援的偵錯案例。

不支援的工作流程設計工具偵錯案例如下：

- 在編輯程式碼之後，就無法繼續執行。

- 無法從工作流程的任何一點繼續執行 (設定下一個)。

- 要等到抵達游標處之後才能繼續執行 (執行至游標處)。

- 工作流程設計工具無法用來偵錯以程式碼 (而不使用設計工具) 所建立的工作流程。

- 在舊版的 Windows Workflow Foundation (WF) 中建立的工作流程無法在.NET Framework 4 的設計工具中偵錯。

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