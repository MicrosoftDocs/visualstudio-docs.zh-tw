---
title: TF 版本控制
description: 使用 Team Foundation 版本控制連線到 Team Foundation Server 或 Visual Studio Team Services。
author: asb3993
ms.author: amburns
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: f892209faeb06ca703d28016457e9ba4ab86ccda
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="connecting-to-team-foundation-version-control"></a>連線到 Team Foundation 版本控制 

Visual Studio Team Services (VSTS) 和 Team Foundation Server (TFS) 提供兩個模型的版本控制：Git 為分散式版本控制，Team Foundation 版本控制 (TFVC) 為集中式版本控制。 本文提供以 Visual Studio for Mac 使用 Team Foundation 版本控制的概觀和起始點。

> [!NOTE]
> **注意**：Team Foundation 版本控制支援目前為預覽版，某些功能尚無法完全運作。 將會有更多的變更！

## <a name="requirements"></a>需求

* Visual Studio for Mac 7.5 或更新版本。
* Visual Studio Team Servers 或 Team Foundation Server 2013 和更新版本
* Visual Studio Team Services 或 Team Foundation Server 中的專案已設定為使用 Team Foundation 版本控制。

## <a name="installation"></a>安裝

從 Visual Studio for Mac 內選擇 [Visual Studio] > [延伸模組...] 功能表。 搜尋「TF 版本控制」並安裝 **Team Foundation 版本控制**延伸模組。 當提示時，重新啟動 IDE。

## <a name="using-the-add-in"></a>使用增益集

安裝延伸模組之後，請選取 [版本控制] > [TFS/VSTS] > [連線到 Team Foundation 版本控制...] 功能表。 

![新增 TFVC 伺服器](media/tfvc-add-remove-server.png)


請選擇 Visual Studio Team Services 或 Team Foundation Server 其中之一來開始：

![以 TFVC 服務器連線](media/tfvc-choose-server-type.png)

輸入您的認證： 

![登入 TFVC 伺服器](media/tfvc-login.png)

然後選擇您想要存取的專案： 

![選擇專案](media/tfvc-choose-projects.png)

若要繼續，請關閉對話方塊，然後使用 [版本控制] > [TFS/VSTS] > [原始檔控制總管] 功能表來瀏覽來源。

> [!WARNING]
> **已知問題**：在此預覽版本中，第一次開啟原始檔控制總管時，您必須先建立新的工作區。

![來源總管](media/tfvc-source-explorer.png)

從 [原始程式碼總管] 中，您可以瀏覽伺服器上的原始程式碼，並執行下列動作：

- 管理工作區 (建立、編輯或刪除)。
- 在專案結構之間巡覽。
- 對應專案。
- 取得專案。
- 鎖定與解除鎖定檔案。
- 重新命名檔案。
- 刪除檔案。
- 新增新檔案。
- 簽出。
- 簽入。
- 檢視歷程記錄變更。
- 比較變更。

## <a name="creating-a-new-workspace"></a>新增新的工作區

在 [原始檔控制總管] 中，按一下 [管理工作區] 按鈕。 

![管理工作區](media/tfvc-manage-workspaces.png)

按一下 [新增] 以建立新的工作區。

![建立工作區](media/tfvc-create-workspace.png)

提供工作區的名稱，然後按一下 [新增工作資料夾] 以對應專案至您電腦上的本機資料夾。

完成之後，按一下 [確定]，然後關閉 [管理工作區] 對話方塊。 現在您可以透過 [原始程式碼總管] 取得檔案並開始使用。