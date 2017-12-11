---
title: "Visual Studio Tools for Unity Azure 逐步解說 | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7921D4C7-5526-42F5-8E03-82D3E33A893F
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: a7e12508537a3bcda1df7997ba9e390b75b9beaf
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="using-azure-easy-tables-with-unity-walkthrough"></a>搭配使用 Azure 簡易表和 Unity 逐步解說

![範例遊戲螢幕擷取畫面](media/vstu_azure-test-sample-game-image2.png)

## <a name="introduction"></a>簡介

Azure 提供可調整規模的解決方案，將遙測和其他遊戲資料儲存在雲端。 在 Unity 2017 版中，由於 Unity 的 .NET 4.6 支援允許使用 Azure Mobile Client SDK，因此 Azure 整合比過去更容易。

這些步驟將逐步完成使用 Azure 將遙測和排行榜資料儲存在雲端之 Unity 專案的設定程序。

> [!NOTE]
> 此專案需要 Unity 2017 中的「實驗性」.NET 4.6 Mono 指令碼執行階段。 [Unity 指出不久這將成為預設值](https://forum.unity3d.com/threads/future-plans-for-the-mono-runtime-upgrade.464327/)，但目前它仍標示為「實驗性」，而且您可能會遇到問題。

> 本逐步解說示範如何從 Unity PC 組建連線到 Azure 行動應用程式後端。 在撰寫本文件時，已知有使得此專案無法在 Mac 和 Android 平台上運作的問題。 雖然這些已知問題未來將獲得修正，但何時修正並不確定。 如需詳細資訊，請前往 Unity [實驗性指令碼論壇](https://forum.unity3d.com/forums/experimental-scripting-previews.107/)。

## <a name="download-the-completed-project"></a>下載已完成的專案

GitHub 上提供已完成的專案。 不過，本逐步解說假設您從空的新專案開始，並將視需要提供下載資產的連結。

## <a name="walkthrough-steps"></a>逐步解說步驟

1. [在 Azure 中設定簡易表](visual-studio-tools-for-unity-azure-configure.md)
2. [建立簡易表](visual-studio-tools-for-unity-azure-setup.md)
3. [準備開發環境](visual-studio-tools-for-unity-azure-prepare.md)
4. [建立資料模型類別](visual-studio-tools-for-unity-azure-data.md)
5. [實作 Azure MobileServiceClient](visual-studio-tools-for-unity-azure-mobile-client.md)
6. [更新 Unity Mono 安全性憑證存放區](visual-studio-tools-for-unity-azure-security.md)
7. [測試用戶端連線](visual-studio-tools-for-unity-azure-connection.md)
7. [匯入範例遊戲資產](visual-studio-tools-for-unity-azure-game-assets.md)
8. [測試範例遊戲](visual-studio-tools-for-unity-azure-game.md)
9. [RaceScene 說明](visual-studio-tools-for-unity-azure-racescene.md)
10. [HeatmapScene 說明](visual-studio-tools-for-unity-azure-heatmapscene.md)
11. [LeaderboardScene 說明](visual-studio-tools-for-unity-azure-leaderboardscene.md)


## <a name="next-step"></a>後續步驟
* [在 Azure 中設定簡易表](visual-studio-tools-for-unity-azure-configure.md)
