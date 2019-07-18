---
title: 在 Visual Studio for Mac 中設定多個啟始專案
description: 本文描述如何設定多個專案以在執行或偵錯時啟動。
author: sayedihashimi
ms.author: sayedha
ms.date: 02/21/2019
ms.topic: conceptual
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: cd76eaf30dd0151216a503bbaf1d76414ed56eef
ms.sourcegitcommit: 9753c7544cec852ca5efd0834e0956d9e53a5734
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "67043500"
---
# <a name="set-multiple-startup-projects"></a>設定多個啟始專案

Visual Studio for Mac 可讓您指定要在對解決方案進行偵錯或執行時啟動多個專案。

## <a name="to-set-multiple-startup-projects"></a>設定多個啟動專案

1. 在 Solution Pad 中，選取解決方案 (最上層節點)。

2. 以滑鼠右鍵按一下解決方案節點，然後選取 [設定啟始專案]  ：

   ![選取 [設定啟始專案]](media/startup-proj-ctx-menu.png)

3. [建立解決方案回合組態]  對話方塊隨即開啟。 此對話方塊可讓您為解決方案建立具有名稱的新解決方案回合組態。 您可以使用任何您想要的名稱。 預設名稱為 `Multiple Projects`。

   ![[建立解決方案回合組態] 對話方塊](media/create-sln-run-config.png)

4. 選取 [建立回合組態]  。 [解決方案選項]  對話方塊隨即開啟，並選取了新的解決方案回合組態：

   ![[解決方案選項] 對話方塊](media/sln-options-run-config-multi-projects.png)

5. 選取您在 Visual Studio for Mac 中對應用程式進行偵錯或執行時，要啟動的專案：

   ![[解決方案選項] 對話方塊，已選取其中的專案](media/sln-options-run-config-multi-projects-configured.png)

6. 選取 [確定]  。 新的解決方案回合組態會設定為使用中的回合組態：

   ![設定為在偵錯或執行時，要啟動多個專案的解決方案](media/startup-project-configured.png)

   您可以看到設定是要啟動兩個專案，因為這兩個專案在 Solution Pad 中都以**粗體**顯示。 在工具列中，目前的解決方案回合組態是設定為新的回合組態。

## <a name="next-steps"></a>後續步驟

- [在 Visual Studio for Mac 中編譯和建置](compiling-and-building.md)
- [了解組建組態](configurations.md)
