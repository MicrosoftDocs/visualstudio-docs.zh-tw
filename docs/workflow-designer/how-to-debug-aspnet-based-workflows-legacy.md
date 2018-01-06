---
title: "如何： 偵錯 ASP.NET 型工作流程 （舊版） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: aspnet
ms.openlocfilehash: 36905d8716b2f6a0fd961f668b7b5ca7c3ef623d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>HOW TO：ASP.NET 工作流程偵錯 (舊版)
本主題描述如何在舊版 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 中偵錯 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 型 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 應用程式，該應用程式是以 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 或 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 為目標。  
  
 您可以針對在 ASP.NET 中啟動的舊版工作流程，或是藉由附加至裝載工作流程的處理序而發行為 Web 服務的舊版工作流程進行偵錯。  
  
### <a name="to-debug-an-aspnet-based-workflow"></a>若要偵錯 ASP.NET 工作流程  
  
1.  啟用偵錯 ASP.NET 應用程式，藉由設定**偵錯 = true** web.config 檔案中。  
  
2.  將工作流程程式庫設為啟始專案，並在工作流程中設定中斷點。  
  
3.  在工作流程專案屬性中輸入預設網頁的 URL**偵錯**選項**與外部 URL 啟動瀏覽器**文字方塊。  
  
4.  選取**附加至處理序**上**偵錯**功能表。  
  
5.  選取要從附加至處理序**可用的處理序**清單。  
  
     附加至裝載工作流程的 w3wp.exe、webdev.webserver 或 aspnet_wp 處理序。  
  
6.  按一下**選取**旁**附加至**文字方塊。  
  
     **選取程式碼類型** 對話方塊隨即出現。  
  
7.  選取**偵錯這些程式碼類型**選取**工作流程**。  
  
8.  按一下 [確定 **Deploying Office Solutions**]。  
  
9. 按一下 [附加] 。  
  
10. 在瀏覽器中開啟預設網頁，並啟動工作流程。  
  
## <a name="see-also"></a>請參閱  
 [叫用 Visual Studio Debugger for Windows Workflow Foundation （舊版）](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [如何： 在工作流程 （舊版） 中設定中斷點](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [偵錯舊版工作流程](../workflow-designer/debugging-legacy-workflows.md)