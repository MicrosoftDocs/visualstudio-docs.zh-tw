---
title: "Visual Studio Tools for Unity Azure 逐步解說遊戲資產 | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: C06FAB2E-F592-4EFF-B96A-58858C92DCEB
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 3b1ad3d7dc6af48986e8b10278a8b8135843239d
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="import-sample-game-assets"></a>匯入範例遊戲資產

現在已測試核心功能並證明運作正常，接下來將匯入範例遊戲資產。

## <a name="import-package"></a>匯入套件

1. 下載[範例遊戲資產套件](https://github.com/dantogno/UnityAzureSample/blob/master/Azure%20Easy%20tables%20sample%20game%20assets.unitypackage)。

2. 確定您的 Unity 專案已開啟，然後巡覽至下載位置，並按兩下該檔案。 這會在 Unity 中顯示 [匯入] 對話方塊。

3. 按一下 [全部]，然後按一下 [匯入]。 等候產生的進度列完成。

  ![匯入套件](media/vstu_azure-import-sample-assets-image1.png)

## <a name="add-scenes-to-build-settings"></a>將場景新增至組建設定

一旦完成匯入檔案，必須在 Unity 專案的 [組建設定] 中新增必要的場景檔案。

1. 在 Unity 的 [專案] 視窗中，巡覽至 **Azure Easy Tables sample game assets/Scenes** 目錄。

2. 從 Unity 功能表，選取 [檔案] > [組建設定...]。這會顯示 [組建設定] 對話方塊。

3. 將 **HeatmapScene**、**LeaderboardScene**、**MenuScene** 和 **RaceScene** 檔案從 [專案] 視窗拖曳至 [組建設定] 對話方塊中的 [Scenes In Build] (組建中的場景) 區段。

  ![匯入套件](media/vstu_azure-import-sample-assets-image2.png)

4. 從 Unity 功能表，選取 [檔案] > [儲存專案] 確定儲存組建設定。

## <a name="next-step"></a>後續步驟

* [測試範例遊戲](visual-studio-tools-for-unity-azure-game.md)