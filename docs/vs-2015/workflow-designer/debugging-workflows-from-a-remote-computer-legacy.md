---
title: 偵錯工作流程，從遠端電腦 （舊版） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f37e2f1d785399283e9da8f4ecb853f0728d9830
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976939"
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>從遠端電腦偵錯工作流程 (舊版)
本主題描述如何偵錯使用舊版 [!INCLUDE[wf](../includes/wf-md.md)] 所建置的遠端舊版 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 應用程式。 當您的應用程式需要以 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 或 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 為目標時，請使用舊版 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]。  
  
 當您安裝[!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)]，其中的元件安裝選項可用來安裝[!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)]偵錯工具的[!INCLUDE[wf](../includes/wf-md.md)]。 這會安裝遠端偵錯元件。 這些遠端偵錯元件必須安裝在要進行遠端工作流程偵錯的目標電腦上。  
  
 此外，包含您在遠端電腦上所偵錯之舊版工作流程之工作流程定義的組件，必須安裝在進行偵錯的來源本機電腦的全域組件快取 (GAC) 中。 例如，如果舊版工作流程是在遠端電腦 A 上執行，而您要從本機電腦 B 偵錯該工作流程，則工作流程定義必須位於電腦 B 的 GAC 中。如此可讓設計工具將執行於遠端電腦 A 之工作流程的工作流程標記，在電腦 B 上還原序列化並加以顯示。如需全域組件快取的詳細資訊，請參閱 MSDN Library。  
  
 [!INCLUDE[wf2](../includes/wf2-md.md)] 遠端偵錯的運作方式與其他 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 元件的遠端偵錯功能相同。 如需詳細資訊，請參閱[!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)]MSDN Library 中的遠端偵錯。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯舊版工作流程](../workflow-designer/debugging-legacy-workflows.md)