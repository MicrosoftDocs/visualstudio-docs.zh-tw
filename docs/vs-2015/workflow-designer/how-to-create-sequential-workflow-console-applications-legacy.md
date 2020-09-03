---
title: 如何：建立 (舊版) 的連續工作流程主控台應用程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c9e3f97021e742db7b22a400dee0682669b07e4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662720"
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>HOW TO：建立循序工作流程主控台應用程式 (舊版)
依照下列步驟使用 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 提供的舊版 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 來建立循序工作流程主控台應用程式專案。 當您需要以 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 或 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 為目標時，請使用舊版 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]。

### <a name="to-create-a-sequential-workflow-console-application"></a>若要建立循序工作流程主控台應用程式

1. 啟動 Visual Studio。

2. 在 **[檔案]** 功能表上，指向 **[開新檔案]**，再選取 **[專案]**。

     此時會開啟 [新增專案]**** 對話方塊。

3. 在 [**新增專案**] 視窗頂端的下拉式清單中，選取 [ **.NET Framework 3.0** ] 選項或 [ **.NET Framework 3.5** ] 選項，以存取舊版設計工具。

    > [!NOTE]
    > 中的預設選項 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 是 **.NET Framework 4**。 這個選項是用來建立以 [!INCLUDE[wf](../includes/wf-md.md)] 為目標的 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 應用程式，而不會使用舊版設計工具。

4. 在 [ **專案類型** ] 窗格中，選取 [Visual c # 專案] 或 [Visual Basic 專案 (**其他語言**) ]，然後選取 [ **工作流程**]。

5. 在 [ **範本** ] 窗格中，選取 [ **連續工作流程主控台應用程式**]。

6. 在 [ **名稱** ] 方塊中，輸入專案的描述性名稱，以方便識別。

7. 在 [ **位置** ] 方塊中，輸入您要用來儲存專案的目錄，或按一下 **[流覽]** 流覽至該目錄。

     接著會開啟 Windows Form 設計工具，顯示您剛剛建立之專案的 Form1。

8. 按一下 [確定]  。

     工作流程設計工具會開啟並顯示您所建立的循序工作流程之設計介面。

9. 將 [ **工具箱** ] 中的活動拖曳至 **放置活動** 指定區域中的設計介面。

## <a name="see-also"></a>另請參閱
 [建立舊版工作流程專案](../workflow-designer/creating-legacy-workflow-projects.md)[開發工作流程](https://msdn.microsoft.com/557bcb1f-a7ab-49f6-8df7-2706b7001301)