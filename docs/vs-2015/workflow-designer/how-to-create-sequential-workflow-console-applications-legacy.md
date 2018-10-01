---
title: 如何： 建立循序工作流程主控台應用程式 （舊版） |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 0882a39dfae5639fcfc72adc7ccd976f4d93e30a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490882"
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>HOW TO：建立循序工作流程主控台應用程式 (舊版)
依照下列步驟使用 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 提供的舊版 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 來建立循序工作流程主控台應用程式專案。 當您需要以 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 或 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 為目標時，請使用舊版 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]。  
  
### <a name="to-create-a-sequential-workflow-console-application"></a>若要建立循序工作流程主控台應用程式  
  
1.  啟動 Visual Studio。  
  
2.  在 [檔案] 功能表上，指向 [新增]，然後選取 [專案]。  
  
     [ **新增專案** ] 對話方塊隨即開啟。  
  
3.  選取 **.NET Framework 3.0**選項或 **.NET Framework 3.5**在清單頂端的下拉式選項**新專案**存取舊版設計工具 視窗。  
  
    > [!NOTE]
    >  中的預設選項[!INCLUDE[vs2010](../includes/vs2010-md.md)]已 **.NET Framework 4**。 這個選項是用來建立以 [!INCLUDE[wf](../includes/wf-md.md)] 為目標的 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 應用程式，而不會使用舊版設計工具。  
  
4.  在 [**專案類型**] 窗格中，選取 Visual C# 專案或 Visual Basic 專案 (下**其他語言**)，然後選取**工作流程**。  
  
5.  在 **範本**窗格中，選取**循序工作流程主控台應用程式**。  
  
6.  在 **名稱**方塊中，輸入您的專案，讓您輕鬆地識別的描述性名稱。  
  
7.  在 **位置**方塊中，輸入您要儲存您的專案，或按一下 的目錄**瀏覽**來巡覽找到它。  
  
     接著會開啟 Windows Form 設計工具，顯示您剛剛建立之專案的 Form1。  
  
8.  按一下 [確定 **Deploying Office Solutions**]。  
  
     工作流程設計工具會開啟並顯示您所建立的循序工作流程之設計介面。  
  
9. 活動拖曳**工具箱**設計介面上要**卸除活動**指定區域。  
  
## <a name="see-also"></a>另請參閱  
 [建立舊版工作流程專案](../workflow-designer/creating-legacy-workflow-projects.md)   
 [開發工作流程](http://msdn.microsoft.com/en-us/557bcb1f-a7ab-49f6-8df7-2706b7001301)