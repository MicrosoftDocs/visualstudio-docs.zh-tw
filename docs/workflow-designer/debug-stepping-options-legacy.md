---
title: 工作流程設計工具的偵錯逐步執行選項 （舊版）
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f46c0ab382a0e189c595e6e0f8aeb69c71814faf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="debug-stepping-options-legacy"></a>偵錯逐步執行選項 (舊版)

本主題描述如何偵錯舊版的 Windows 工作流程設計工具中擁有並行活動的 Windows Workflow Foundation (WF) 應用程式。 當您需要以.NET Framework 3.5 版或 WinFX 為目標時，請使用舊版工作流程設計工具。

當您正在偵錯舊版的活動，具有並行執行，例如**ParallelActivity**或**ConditionedActivityGroup**，您可以使用下列兩個選項的其中一個選項逐步執行程式碼.

-   **分支逐步執行。** 這個逐步模式可讓您逐步執行和偵錯特定分支的複合活動，例如**ParallelActivity**或**ConditionalActivityGroup**活動。 使用此選項偵錯時，由於工作流程中同時執行其他活動，因此您將不會注意到控制項中發生變化。 當工作流程中的其他活動可能正在同時執行時，偵錯工具只會逐步執行目前選取之分支中的活動。 例如，根據預設，在最左邊的分支**ParallelActivity**活動及第一個子活動的**ConditionedActivityGroup**活動用於逐步執行。 如果使用者想要偵錯任何其他分支或子活動，必須在該分支或子活動上放置明確的中斷點。 觸發 (Trigger) 中斷點時，逐步執行會在該分支中繼續。

-   **執行個體逐步執行。** 這個逐步模式可讓您逐步執行和偵錯工作流程中的並行執行活動。 使用此選項時，您會在工作流程內的並行執行活動執行時發現控制權的改變。

預設會選取分支逐步執行選項，使用者在偵錯舊版工作流程時，可在這兩種選項間切換。

您在偵錯舊版狀態機器工作流程時，應選取執行個體逐步執行選項。

## <a name="see-also"></a>另請參閱

- [偵錯舊版工作流程](../workflow-designer/debugging-legacy-workflows.md)
- [如何：變更偵錯逐步執行選項 (舊版)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)