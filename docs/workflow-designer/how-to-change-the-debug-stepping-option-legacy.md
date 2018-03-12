---
title: "如何： 變更偵錯逐步執行選項 （舊版） |Microsoft 文件"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ea687b0a08aa4697ac9f7c7b0aca875af131a561
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>HOW TO：變更偵錯逐步執行選項 (舊版)
本主題描述如何變更偵錯逐步執行選項[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]舊版的 Windows 工作流程設計工具中具有並行動作的應用程式。 當您需要以 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 或 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 為目標時，請使用舊版 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]。

 當您正在偵錯舊版的活動，具有並行執行，例如**ParallelActivity**或**ConditionedActivityGroup**，您可以使用其中一個選項逐步執行程式碼。

 依照下列步驟變更舊版工作流程專案中的偵錯逐步執行選項。

## <a name="procedures"></a>程序

#### <a name="to-change-the-debug-stepping-option"></a>若要變更偵錯逐步執行選項

1.  啟動 Visual Studio。

2.  開啟現有的舊版工作流程專案或建立新的專案，使其利用並行活動並以 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 為目標。

3.  在**工作流程**功能表在舊版[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]，指向 **偵錯**，然後指向**逐步執行選項**。

4.  選取 **執行個體**或**分支**。

## <a name="see-also"></a>另請參閱

- [偵錯舊版工作流程](../workflow-designer/debugging-legacy-workflows.md)
- [偵錯逐步執行選項 (舊版)](../workflow-designer/debug-stepping-options-legacy.md)