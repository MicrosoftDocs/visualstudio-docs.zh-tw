---
title: "Visual Studio Tools for Unity Azure 逐步解說遊戲 | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: DA86FC7F-E456-4DFC-84BF-D780421508B9
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 204389c2341c3aa9f729b92b5f3d459e7b101d24
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="test-the-sample-game"></a>測試範例遊戲

此範例遊戲是簡單的賽車遊戲，會記錄玩家行為的相關資料並將它儲存在 Azure 簡易表中。 此範例遊戲也包含場景，會從 Azure 讀取資料並顯現給玩家。

本節只會說明如何進行範例遊戲及確保其運作正常。 後續章節將會進一步說明範例遊戲的運作方式。

## <a name="starting-the-game"></a>啟動遊戲

1. 在 Unity 的 [專案] 視窗中，巡覽至 **Assets/Azure Easy Tables sample game assets/Scenes** 資料夾。

2. 按兩下 **MenuScene** 將它開啟。

3. 在 Unity 的 [遊戲] 視窗中，按一下 [外觀比例] 下拉式清單並選擇 [16:9]。

  ![設定外觀比例](media/vstu_azure-test-sample-game-image1.png)

4. 按一下 [播放] 按鈕，在 Unity 編輯器中執行遊戲。


## <a name="complete-a-race"></a>完成一場比賽

在檢視排行榜或熱度圖之前，最好至少完成一場比賽以建立一些範例資料。

1. 在 Unity 編輯器中執行遊戲時，按一下 [Race!] (比賽!) 按鈕開始新的比賽。

2. 使用 **WASD** 或**方向鍵**來駕駛，並沿著賽車場順時針完成一圈。由於這是範例，請務必沿途碰撞一些牆。 Unity 主控台中的偵錯輸出應該會指出何時記錄碰撞。

  >[!NOTE]
  > 如果您因翻車而無法繼續，請按一下 [重新啟動]。 只有完成一圈，才會將資料傳送至 Azure。

  ![開始比賽](media/vstu_azure-test-sample-game-image2.png)

3. 通過黑白格終點線之後，遊戲應該顯示 [已完成] 訊息。 此時會將撞車資料上傳至 Azure。

4. 如果您已達成前 10 名最快單圈時間，系統會提示您針對高分記錄輸入名稱。 輸入您的名稱，然後按一下 [送出]。

  ![開始比賽](media/vstu_azure-test-sample-game-image3.png)

## <a name="view-the-heatmap"></a>檢視熱度圖

1. 從賽車場景按一下 [View Crash Heatmap] (檢視撞車熱度圖) 按鈕，或從主功能表選取 [Crash Heatmap] (撞車熱度圖)。

2. 熱度圖場景會從 Azure 的 CrashInfo 資料表載入資料，並在玩家碰撞賽車場牆壁的位置顯示透明的紅色球體。如果在重疊的區域發生多起撞車，球體看起來應該會更亮。

  ![熱度圖](media/vstu_azure-test-sample-game-image4.png)

## <a name="view-the-leaderboard"></a>檢視排行榜

1. 從賽車場景或主功能表按一下 [排行榜] 按鈕。

2. 排行榜場景會從 Azure 的 HighScoreInfo 資料表載入高分記錄，並顯示每個高分記錄項目的玩家名稱和單圈時間。

  ![排行榜](media/vstu_azure-test-sample-game-image5.png)

## <a name="next-step"></a>後續步驟

* [RaceScene 說明](visual-studio-tools-for-unity-azure-racescene.md)
