---
title: 不支援的偵錯案例
description: 瞭解工作流程設計工具中不支援的偵錯工具案例，例如「在編輯程式碼後無法繼續執行」。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 70620528bd3e2d50b85d67eef5990d9843ea5178
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875129"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>工作流程設計工具中不支援的偵錯情況

工作流程設計工具不支援下列調試案例：

- 在編輯程式碼之後，就無法繼續執行。

- 無法從工作流程的任何一點繼續執行 (設定下一個)。

- 要等到抵達游標處之後才能繼續執行 (執行至游標處)。

- 工作流程設計工具無法用來偵錯以程式碼 (而不使用設計工具) 所建立的工作流程。

- 在舊版 Windows Workflow Foundation 中建立的工作流程 (WF) 無法在 .NET Framework 4 或更新版本中進行調試。

- 活動或 <xref:System.Activities.Statements.Flowchart> 節點之間的連結上無法定義中斷點。

- 偵錯期間不可使用剪貼簿。

- 在複製或貼上活動時，不會保留中斷點。

- 呼叫堆疊視窗中無法設定工作流程中斷點。

- 在設計工具中建立中斷點時，不會使用 [**新增中斷點**] 對話方塊中的 [**行**] 和 [**字元**] 設定。

- 中斷點視窗或捷徑功能表不支援以下資料行或工作流程偵錯的選項：

  - 條件

  - 叫用計數

  - 叫用時

  - 函式

  - 資料

  - 處理序

  - 移至反組譯碼
