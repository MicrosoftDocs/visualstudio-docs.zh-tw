---
title: 作法：建立工作流程活動程式庫（舊版） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, activity library projects
- workflow activity libraries
- projects, workflow activity libraries
ms.assetid: fb5aa940-2ae8-4b52-b52c-51c20861a7b4
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5bc4566c1ea520ac1050227ac8e4c0aee22e617
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604954"
---
# <a name="how-to-create-a-workflow-activity-library-legacy"></a>作法：建立工作流程活動程式庫 (舊版)
依照下列步驟使用 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 提供的舊版 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 來建立工作流程活動程式庫專案。 當您需要以 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 或 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 為目標時，請使用舊版 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]。

### <a name="to-create-a-workflow-activity-library-project"></a>若要建立工作流程活動程式庫專案

1. 啟動 Visual Studio。

2. 在 [檔案] 功能表上，指向 [新增]，然後選取 [專案]。

     [ **新增專案** ] 對話方塊隨即開啟。

3. 在 [**新增專案**] 視窗頂端的下拉式清單中，選取 [ **.NET Framework 3.0** ] 選項或 [ **.NET Framework 3.5** ] 選項，以存取舊版設計工具。

    > [!NOTE]
    > @No__t_0 中的預設選項為 **.NET Framework 4**。 這個選項是用來建立以 [!INCLUDE[wf](../includes/wf-md.md)] 為目標的 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 應用程式，而不會使用舊版設計工具。

4. 在 **專案類型** 窗格中， C#選取 視覺效果 或 Visual Basic （在 **其他語言** 底下），然後選取 **工作流程**

5. 在 [**範本**] 窗格中，選取 [**工作流程活動程式庫**]。

6. 在 [**名稱**] 方塊中，輸入專案的描述性名稱，使其易於識別。

7. 在 [**位置**] 方塊中，輸入您要儲存專案的目錄，或按一下 **[流覽]** 以流覽至它。

     如果您想要為專案建立方案目錄，請選取 [**為方案建立目錄**] 核取方塊，並在 [**方案名稱**] 方塊中輸入名稱。

8. 按一下 [確定]。

## <a name="see-also"></a>另請參閱
 [使用舊版活動設計](../workflow-designer/using-the-legacy-activity-designer.md)工具[建立舊版工作流程專案](../workflow-designer/creating-legacy-workflow-projects.md)[舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md) [Windows Workflow Foundation 活動](https://msdn.microsoft.com/192c4c1e-afb6-4f58-ab11-2b5bbbc2d2c0)[開發工作流程活動](https://msdn.microsoft.com/19876dfc-dfa5-4d52-b1f5-1d087474cc52)