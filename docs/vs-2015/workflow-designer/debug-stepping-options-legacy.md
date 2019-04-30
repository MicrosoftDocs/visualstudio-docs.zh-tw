---
title: 偵錯逐步執行選項 （舊版） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b1f0761ba750146ce7f8cc52e6992dae689f7779
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976953"
---
# <a name="debug-stepping-options-legacy"></a>偵錯逐步執行選項 (舊版)
本主題描述如何偵錯在舊版 [!INCLUDE[wf](../includes/wf-md.md)] 中擁有並行活動的 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 應用程式。 當您需要以 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 或 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 為目標時，請使用舊版 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]。  
  
 當您正在偵錯舊版的活動，具有並行執行，例如**ParallelActivity**或是**ConditionedActivityGroup**，您可以使用下列兩個選項的其中一個來逐步執行程式碼.  
  
- **分支逐步執行。** 這個逐步模式可讓您逐步執行和偵錯特定分支的複合活動，例如**ParallelActivity**或**ConditionalActivityGroup**活動。 使用此選項偵錯時，由於工作流程中同時執行其他活動，因此您將不會注意到控制項中發生變化。 當工作流程中的其他活動可能正在同時執行時，偵錯工具只會逐步執行目前選取之分支中的活動。 例如，根據預設，在左邊的分支**ParallelActivity**活動和第一個子活動的**ConditionedActivityGroup**活動用於逐步執行。 如果使用者想要偵錯任何其他分支或子活動，必須在該分支或子活動上放置明確的中斷點。 觸發 (Trigger) 中斷點時，逐步執行會在該分支中繼續。  
  
- **執行個體逐步執行。** 這個逐步模式可讓您逐步執行和偵錯工作流程中的並行執行活動。 使用此選項時，您會在工作流程內的並行執行活動執行時發現控制權的改變。  
  
  預設會選取分支逐步執行選項，使用者在偵錯舊版工作流程時，可在這兩種選項間切換。  
  
  您在偵錯舊版狀態機器工作流程時，應選取執行個體逐步執行選項。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯舊版工作流程](../workflow-designer/debugging-legacy-workflows.md)   
 [如何：變更偵錯逐步執行選項 (舊版)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)