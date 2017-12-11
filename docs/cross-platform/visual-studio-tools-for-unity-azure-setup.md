---
title: "Visual Studio Tools for Unity Azure 逐步解說設定 | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: FFE17FC6-0B47-4A00-A125-01BD49E3873C
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 447f32c2e736084a08223b56f4188ca7c8abeea5
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="create-easy-tables"></a>建立簡易表

現在您在 Azure 上有行動應用程式並已初始化其簡易表，接下來將建立資料表來追蹤從 Unity 遊戲送出的資料。

## <a name="setup-the-crash-heatmap-table"></a>設定撞車熱度圖資料表

1. 在 Azure 入口網站中，按一下 [所有資源]，然後選取您在先前步驟中為簡易表所設定的行動應用程式。

  ![選取行動應用程式](media/vstu_azure-setup-table-schema-image1.png)

2. 向下捲動至 [行動] 標題並選取 [簡易表]。 此時應該不會再出現有關針對簡易表將應用程式初始化的任何通知。  

  ![選取 [簡易表]](media/vstu_azure-setup-table-schema-image2.png)

3. 按一下 [新增] 按鈕。

  ![按一下 [新增]](media/vstu_azure-setup-table-schema-image3.png)

4. 將資料表命名為 "**CrashInfo**"，然後按一下 [確定]。 保留其餘選項的預設設定。

  > [!WARNING]
  > 此名稱必須符合本逐步解說稍後所建立的資料模型類別名稱。

  ![命名並按一下 [確定]](media/vstu_azure-setup-table-schema-image4.png)

5. 建立新的資料表時會宣佈通知。

> [!NOTE]
> 使用簡易表時，資料表結構描述實際上會隨資料新增而動態建立。 這表示不需要在此步驟期間手動設定適當的資料行。

## <a name="setup-the-leaderboard-table"></a>設定排行榜資料表

1. 返回 [簡易表] 刀鋒視窗，然後按一下 [新增] 新增第二個資料表。

  ![新增第二個資料表](media/vstu_azure-setup-table-schema-image10.png)

2. 將新資料表命名為 "**HighScoreInfo**"，然後按一下 [確定]。 保留其餘選項的預設設定。

  > [!WARNING]
  > 此名稱必須符合本逐步解說稍後所建立的資料模型類別名稱。

  ![命名並按一下 [確定]](media/vstu_azure-setup-table-schema-image11.png)

3. 建立新的資料表時會宣佈通知。


## <a name="next-step"></a>後續步驟

* [準備開發環境](visual-studio-tools-for-unity-azure-prepare.md)
