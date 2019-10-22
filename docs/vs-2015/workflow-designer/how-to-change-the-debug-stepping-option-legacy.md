---
title: 如何：變更調試逐步執行選項（舊版） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5126b3dc45d33471080ae154e06f4a327e21fef7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663442"
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>HOW TO：變更偵錯逐步執行選項 (舊版)
本主題描述如何在具有並行動作的舊版 [!INCLUDE[wf](../includes/wf-md.md)] 中變更 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 應用程式的偵錯逐步執行選項。 當您需要以 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 或 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 為目標時，請使用舊版 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]。

 當您要對具有並存執行的舊版活動（例如**ParallelActivity**或**ConditionedActivityGroup**）進行偵錯工具時，您可以使用兩個選項的其中之一來逐步執行程式碼。

 依照下列步驟變更舊版工作流程專案中的偵錯逐步執行選項。

## <a name="procedures"></a>程序

#### <a name="to-change-the-debug-stepping-option"></a>若要變更偵錯逐步執行選項

1. 啟動 Visual Studio。

2. 開啟現有的舊版工作流程專案或建立新的專案，使其利用並行活動並以 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 或 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] 為目標。

3. 在舊版 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 的 [**工作流程**] 功能表上，指向 [ **Debug**]，然後指向 [**逐步執行選項**]。

4. 選取 [**實例**] 或 [**分支**]。

## <a name="see-also"></a>請參閱
 [調試舊版工作流程](../workflow-designer/debugging-legacy-workflows.md) [Debug 逐步執行選項（舊版）](../workflow-designer/debug-stepping-options-legacy.md)