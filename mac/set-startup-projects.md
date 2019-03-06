---
title: 在 Visual Studio for Mac 中設定多個啟始專案
description: 本文描述如何設定多個專案以在執行或偵錯時啟動。
author: sayedihashimi
ms.author: sayedha
ms.date: 02/21/2019
ms.topic: conceptual
ms.prod: visual-studio-mac-dev16
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: 84581fb3f6e33d22f0895b807998120ea7ca0cb7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56724044"
---
# <a name="how-to-set-multiple-startup-projects"></a>作法：設定多個啟始專案
Visual Studio for Mac 可讓您指定如何在針對解決方案進行偵錯或執行時啟動多個專案。

## <a name="to-set-multiple-startup-projects"></a>設定多個啟動專案
1.  在 **Solution Pad** 中，選取解決方案 (最上層節點)。

2. 選擇解決方案節點的操作 (以滑鼠右鍵按一下) 功能表，然後選擇 [設定啟始專案...]。

   ![[設定啟始專案] 操作功能表](media/startup-proj-ctx-menu.png)

3. [建立解決方案回合組態] 對話方塊隨即出現。 這個對話方塊會為解決方案建立具有新名稱的解決方案回合組態。 您可以使用您喜歡的任何名稱；預設名稱是 `Multiple Projects`。

   ![[建立解決方案回合組態] 對話方塊](media/create-sln-run-config.png)

4. 按一下 [建立回合組態]。 [解決方案選項] 對話方塊隨即開啟，並選取了新的解決方案回合組態。

   ![[解決方案選項] 對話方塊](media/sln-options-run-config-multi-projects.png)

5. 選取您在 Visual Studio for Mac 中針對應用程式進行偵錯或執行時，要啟動的專案。

   ![已設定回合組態的 [解決方案選項] 對話方塊](media/sln-options-run-config-multi-projects-configured.png)

6. 按一下 [確定 **Deploying Office Solutions**]。 將會關閉此對話方塊，而新的解決方案回合組態會設定為使用中回合組態。

   ![其中多個專案設定為在偵錯或執行時啟動的解決方案](media/startup-project-configured.png) 您可以看到這兩個專案都設定為啟動，因為這兩個專案在 **Solution Pad** 中會以**粗體**顯示。 在工具列中，新回合組態會設定為目前的解決方案回合組態。

## <a name="next-steps"></a>後續步驟

- [在 Visual Studio for Mac 中編譯和建置](compiling-and-building.md)
- [了解組建組態](configurations.md)