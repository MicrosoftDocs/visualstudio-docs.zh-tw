---
title: 舊版工作流程的調試 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40ae0a08e1623e1b90046d164d8bfe04eaf67229
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656858"
---
# <a name="debugging-legacy-workflows"></a>偵錯舊版工作流程
如果您在 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 中使用舊版 [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] 來建置以 .NET Framework 3.0 或 3.5 為目標的 [!INCLUDE[wf](../includes/wf-md.md)] 應用程式，您可以像任何其他程式一樣，藉由設定中斷點、附加至處理序，並檢查執行緒和呼叫堆疊，來偵錯您的工作流程。 您也可以選擇遠端偵錯。

> [!NOTE]
> 如果您的電腦上曾經安裝及解除安裝多個版本的 Visual Studio，WF3 偵錯會因為下列兩種可能性之一而失敗：
>
> - 未達到您的中斷點。
>   - 畫面顯示下列訊息：
>
>   **無法在 web 伺服器上啟動調試。未正確安裝偵錯工具。 無法對要求的程式碼類型進行偵錯工具。 執行安裝程式以安裝或修復偵錯工具。**
>
>   如果在偵錯 .NET Framework 3.0 或 3.5 工作流程時，發生上述任一案例，則執行 Visual Studio 安裝的修復。

 [!INCLUDE[wf2](../includes/wf2-md.md)] 會與以下標準 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 偵錯視窗整合：

- **中斷點**：如預期般運作，但您指定了函數名稱的活動。

- **呼叫堆疊**：已修改以提供在工作流程實例中執行之活動的大綱。 [**呼叫堆疊**] 視窗中的專案是執行中活動的深度優先搜尋。 您可以按兩下項目，將焦點放在選取的活動上。

- **執行緒**：提供正在進行調試之工作流程實例的實例識別碼。

  Visual Studio for Windows Workflow Foundation 不支援以下偵錯功能：

- 設計介面上的條件中斷點。

- 快速監看式。

- 設定 Next 陳述式。

- 執行至游標處。

- 編輯後繼續。

- Just-In-Time 偵錯。

- 混合模式偵錯。

## <a name="in-this-section"></a>本章節內容
 [叫用 Visual Studio Debugger for Windows Workflow Foundation (舊版)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)

 [停用 Visual Studio Debugger for Windows Workflow Foundation (舊版)](../workflow-designer/disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)

 [如何：ASP.NET 工作流程偵錯 (舊版)](../workflow-designer/how-to-debug-aspnet-based-workflows-legacy.md)

 [如何：在工作流程中設定中斷點 (舊版)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)

 [從遠端電腦偵錯工作流程 (舊版)](../workflow-designer/debugging-workflows-from-a-remote-computer-legacy.md)

 [偵錯逐步執行選項 (舊版)](../workflow-designer/debug-stepping-options-legacy.md)

 [如何：變更偵錯逐步執行選項 (舊版)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)