---
title: 如何：建立順序工作流程程式庫（舊版） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflows, creating library
- workflows, sequential workflow library
- projects, sequential workflow library
- sequential workflow libraries
ms.assetid: 9433ccf3-1eab-4d53-90ff-2e7b2341676c
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: adc2e71678e6892d12640a3153f24bfb90dfa429
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663405"
---
# <a name="how-to-create-a-sequential-workflow-library-legacy"></a>HOW TO：建立循序工作流程程式庫 (舊版)
依照下列步驟使用 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 提供的舊版 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 來建立循序工作流程程式庫專案。 當您需要以 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 或 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 為目標時，請使用舊版 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]。

### <a name="to-create-a-sequential-workflow-library-project"></a>若要建立循序工作流程程式庫專案

1. 啟動 Visual Studio。

2. 在 [檔案] 功能表上，指向 [新增]，然後選取 [專案]。

     [ **新增專案** ] 對話方塊隨即開啟。

3. 在 [**新增專案**] 視窗頂端的下拉式清單中，選取 [ **.NET Framework 3.0** ] 選項或 [ **.NET Framework 3.5** ] 選項，以存取舊版設計工具。

    > [!NOTE]
    > @No__t_0 中的預設選項為 **.NET Framework 4**。 這個選項是用來建立以 [!INCLUDE[wf](../includes/wf-md.md)] 為目標的 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 應用程式，而不會使用舊版設計工具。

4. 在 **專案類型** 窗格中， C#選取 視覺效果 或 Visual Basic （在 **其他語言** 底下），然後選取 **工作流程**

5. 在 [**範本**] 窗格中，選取 [**連續工作流程程式庫**]。

6. 在 [**名稱**] 方塊中，輸入專案的描述性名稱，使其易於識別。

7. 在 [**位置**] 方塊中，輸入您要儲存專案的目錄，或按一下 **[流覽]** 以流覽至它。

     如果您想要為專案建立方案目錄，請選取 [**為方案建立目錄**] 核取方塊，並在 [**方案名稱**] 方塊中輸入名稱。

8. 按一下 [確定]。

## <a name="see-also"></a>請參閱
 [建立舊版工作流程專案](../workflow-designer/creating-legacy-workflow-projects.md)[工作流程撰寫樣式](https://msdn.microsoft.com/aacf4ec6-da05-4974-958a-974769dda739)