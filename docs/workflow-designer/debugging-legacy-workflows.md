---
title: "偵錯舊版工作流程 |Microsoft 文件"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4898e8f720143bd60337c9fe6bed20a7489c0d04
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="debugging-legacy-workflows"></a>偵錯舊版工作流程

如果您使用舊版的 Windows 工作流程設計工具中[!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)]建置[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]應用程式，以 Framework 3.0 或 3.5，您可以偵錯您的工作流程類似任何其他程式藉由設定中斷點、 附加至處理序，並檢查執行緒和呼叫堆疊。 您也可以選擇遠端偵錯。

> [!NOTE]
> 如果您的電腦上曾經安裝及解除安裝多個版本的 Visual Studio，WF3 偵錯會因為下列兩種可能性之一而失敗：
>
> -   未達到您的中斷點。
> -   畫面顯示下列訊息：
>
> **無法開始偵錯 web 伺服器上。未正確安裝偵錯工具。無法偵錯所要求的程式碼型別。執行安裝程式來安裝或修復偵錯工具。**
>
> 如果在偵錯 .NET Framework 3.0 或 3.5 工作流程時，發生上述任一案例，則執行 Visual Studio 安裝的修復。

 [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] 會與以下標準 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 偵錯視窗整合：

-   **中斷點**： 運作不如預期，但是您指定用來將函式名稱的活動。

-   **呼叫堆疊**： 已修改以提供工作流程執行個體中執行的活動的外框。 中的項目**呼叫堆疊**視窗是深度優先搜尋執行中活動。 您可以按兩下項目，將焦點放在選取的活動上。

-   **執行緒**： 提供是否正在偵錯工作流程執行個體的執行個體識別碼。

 Visual Studio for Windows Workflow Foundation 不支援以下偵錯功能：

-   設計介面上的條件中斷點。

-   快速監看式。

-   設定 Next 陳述式。

-   執行至游標處。

-   編輯後繼續。

-   Just-In-Time 偵錯。

-   混合模式偵錯。