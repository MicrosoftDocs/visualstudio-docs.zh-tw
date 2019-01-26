---
title: 使用工作流程設計工具偵錯工作流程
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
helpviewer_keywords:
- Visual Studio Workflow Designer [WFD], debugging workflows
- Workflow Designer [WFD], debugging workflows
ms.assetid: d71308cf-d464-4536-8711-0d0a8eadb255
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b06ee7101dcb6b227f8e7f0228730fb0668695b4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54998842"
---
# <a name="debug-workflows-with-the-workflow-designer"></a>偵錯工作流程與工作流程設計工具

**工作流程設計工具**提供偵錯工作流程和自訂活動的能力。 處理程序和行為會類似於預設 Visual Studio 偵錯工具。

## <a name="invoke-the-workflow-debugger"></a>叫用工作流程偵錯工具

一般而言，偵錯工作流程的方式就如同偵錯以其他 Visual Studio 程式語言撰寫的程式。 您可以利用下列方式啟動工作流程偵錯工具：

- 選取  **připojit k procesu**上**偵錯**功能表來選取您的工作流程執行個體執行的主控件程序。 此程序與在 Managed 程式碼中附加至裝載程序一樣。

- 按下**F5**開始執行的工作流程執行個體，或叫用中斷點後繼續執行。

- 使用遠端偵錯。 如需使用遠端偵錯資訊，請參閱[How to:啟用遠端偵錯](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100))。

   > [!NOTE]
   > 如果工作流程應用程式目標設為 x86 架構，而您的電腦執行 64 位元作業系統上裝載，則遠端偵錯將不會運作，除非在遠端電腦上安裝 Visual Studio 或工作流程應用程式的目標變更為**任何 CPU**。

## <a name="step-through-code"></a>逐步執行程式碼

- **中的步驟**:活動會藉由按下逐步**F11**。 偵錯工具會逐步執行任何已定義的處理常式。 如果沒有定義處理常式，則不進入該活動；若為包含其他活動的複合活動，則逐步執行第一個執行中活動。

- **跳離函式：** 逐步跳出活動中，按下**Shift**+**F11**。 逐步跳出活動會將目前活動及其同層級活動執行到完成。 接著偵錯工具會在目前活動的父代上中斷。 從程式碼處理常式逐步跳出時，偵錯工具會在處理常式所關聯的活動上中斷。

- **不進入函式**:不進入函式的活動藉由按下**F10**。 跳出複合活動時，偵錯工具在複合活動的第一個可執行子系上中斷。 不進入非複合活動 (例如，<xref:System.Activities.Statements.Assign> 活動) 時，偵錯工具會執行活動及其相關聯的處理常式，並在下一個活動上中斷。 如果執行的活動是複合活動中最後一個子活動，則在執行後，偵錯工具會在父活動上中斷。

## <a name="debug-with-f5"></a>使用 F5 進行偵錯

如果您正在建置工作流程主控台應用程式，只要按下**F5**開始進行偵錯您的應用程式和工作流程。 如果您要自行建置活動程式庫，您必須指定可執行檔的主應用程式為啟始專案。 若要在 設定啟始專案**方案總管**，以滑鼠右鍵按一下主應用程式的專案名稱，然後選取**設定為啟始專案**。