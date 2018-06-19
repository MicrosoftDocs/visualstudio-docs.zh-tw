---
title: 工作流程設計工具的偵錯舊版工作流程
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 33a8358c5d62b938fc64d608c9b4546ab1745aaa
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970373"
---
# <a name="debugging-legacy-workflows"></a>偵錯舊版工作流程

如果您使用舊版的 Windows 工作流程設計工具在 Visual Studio 中建置 Windows Workflow Foundation (WF) 應用程式，該以 Framework 3.0 或 3.5，您可以偵錯您的工作流程類似任何其他程式所設定中斷點、 附加至處理序，並檢查執行緒和呼叫堆疊。 您也可以選擇遠端偵錯。

> [!NOTE]
> 如果您的電腦上曾經安裝及解除安裝多個版本的 Visual Studio，WF3 偵錯會因為下列兩種可能性之一而失敗：
>
> -   未達到您的中斷點。
> -   畫面顯示下列訊息：
>
> **無法開始偵錯 web 伺服器上。未正確安裝偵錯工具。無法偵錯所要求的程式碼型別。執行安裝程式來安裝或修復偵錯工具。**
>
> 如果在偵錯 .NET Framework 3.0 或 3.5 工作流程時，發生上述任一案例，則執行 Visual Studio 安裝的修復。

 Windows Workflow Foundation 與以下標準 Visual Studio 偵錯視窗整合：

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