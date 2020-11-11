---
title: 設定多個啟始專案
description: 本文描述如何設定多個專案以在執行或偵錯時啟動。
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.topic: how-to
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: df1e088a5e2d0f65d8b72dad0895f1edb1740f1f
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493565"
---
# <a name="set-multiple-startup-projects"></a>設定多個啟始專案

Visual Studio for Mac 可讓您指定要在對解決方案進行偵錯或執行時啟動多個專案。

## <a name="to-set-multiple-startup-projects"></a>設定多個啟動專案

1. 在 [方案] 視窗中，選取最上層節點) 的解決方案 (。

2. 以滑鼠右鍵按一下解決方案節點，然後選取 [設定啟始專案]：

   ![選取 [設定啟始專案]](media/startup-proj-ctx-menu.png)

3. [建立解決方案回合組態] 對話方塊隨即開啟。 此對話方塊可讓您為解決方案建立新的具名解決方案回合組態。 您可以使用任何名稱。 預設名稱為 `Multiple Projects`。

   ![[建立解決方案回合組態] 對話方塊](media/create-sln-run-config.png)

4. 選取 [建立回合組態]。 [解決方案選項] 對話方塊隨即開啟，並已選取新的解決方案回合組態：

   ![[解決方案選項] 對話方塊](media/sln-options-run-config-multi-projects.png)

5. 選取您想在 Visual Studio for Mac 中對應用程式進行偵錯或執行時啟動的專案：

   ![已選取專案的 [解決方案選項] 對話方塊](media/sln-options-run-config-multi-projects-configured.png)

6. 選取 [確定]。 新的解決方案回合組態會被設定為作用中的回合組態：

   ![設定為在偵錯或執行時，要啟動多個專案的解決方案](media/startup-project-configured.png)

   現在這兩個專案已設定為 [啟動]，這是由 [方案] 視窗中顯示為 **粗體** 的兩個專案所代表。 在工具列中，目前的解決方案回合組態是設定為新的回合組態。

## <a name="next-steps"></a>後續步驟

- [在 Visual Studio for Mac 中編譯和建立](compiling-and-building.md)
- [了解組建組態](configurations.md)
