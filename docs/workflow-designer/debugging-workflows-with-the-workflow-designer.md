---
title: 使用工作流程設計工具偵錯工作流程
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Workflow Designer [WFD], debugging workflows
- Workflow Designer [WFD], debugging workflows
ms.assetid: d71308cf-d464-4536-8711-0d0a8eadb255
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7432e02a4c8e133d7d758909a7ea851f90b88841
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650564"
---
# <a name="debug-workflows-with-the-workflow-designer"></a>使用工作流程設計工具的調試工作流程

此**工作流程設計工具**可讓您對工作流程和自訂活動進行調試。 進程和行為類似于預設 Visual Studio 偵錯工具。

## <a name="invoke-the-workflow-debugger"></a>叫用工作流程偵錯工具

一般而言，偵錯工作流程的方式就如同偵錯以其他 Visual Studio 程式語言撰寫的程式。 您可以利用下列方式啟動工作流程偵錯工具：

- 選取 [**調試**程式] 功能表上的 [**附加至進程**]，為您的工作流程實例選取執行中的主控制項進程。 此程序與在 Managed 程式碼中附加至裝載程序一樣。

- 按**F5**開始執行工作流程的實例，或在叫用中斷點後繼續執行。

- 使用遠端偵錯。 如需使用遠端偵錯程式的詳細資訊，請參閱[如何：啟用遠端偵錯](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100))。

   > [!NOTE]
   > 如果工作流應用程式的目標為 x86 架構，並裝載在執行64位作業系統的電腦上，則除非遠端電腦上已安裝 Visual Studio，或工作流程應用程式的目標變更為，**否則遠端偵錯程式將無法運作。任何 CPU**。

## <a name="step-through-code"></a>逐步執行程式碼

- **逐步**執行：按**F11**逐步進入活動。 偵錯工具會逐步執行任何已定義的處理常式。 如果沒有定義處理常式，則不進入該活動；若為包含其他活動的複合活動，則逐步執行第一個執行中活動。

- **跳出：** 按下**Shift** +**F11**跳出活動。 逐步跳出活動會將目前活動及其同層級活動執行到完成。 接著偵錯工具會在目前活動的父代上中斷。 從程式碼處理常式逐步跳出時，偵錯工具會在處理常式所關聯的活動上中斷。

- 不進入函式：按**F10** **跳過活動**。 跳出複合活動時，偵錯工具在複合活動的第一個可執行子系上中斷。 不進入非複合活動 (例如，<xref:System.Activities.Statements.Assign> 活動) 時，偵錯工具會執行活動及其相關聯的處理常式，並在下一個活動上中斷。 如果執行的活動是複合活動中最後一個子活動，則在執行後，偵錯工具會在父活動上中斷。

## <a name="debug-with-f5"></a>使用 F5 進行 Debug

如果您要建立工作流程主控台應用程式，只要按下**F5**即可開始在您的應用程式和工作流程中進行偵測。 如果您要自行建立活動程式庫，您必須指定可執行檔主應用程式做為啟始專案。 若要在**方案總管**中設定啟始專案，請以滑鼠右鍵按一下主控制項的專案名稱，然後選取 [**設定為啟始專案**]。