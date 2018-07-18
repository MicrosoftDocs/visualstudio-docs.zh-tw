---
title: TF 版本控制
description: 使用 Team Foundation 版本控制連線到 Team Foundation Server 或 Visual Studio Team Services。
author: asb3993
ms.author: amburns
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 58d0fc5c31b02574661f8b86a4ae8bcaf393be3a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693769"
---
# <a name="connecting-to-team-foundation-version-control"></a>連線到 Team Foundation 版本控制 

> [!NOTE]
> **注意**：Team Foundation 版本控制支援目前為預覽版，某些功能尚無法完全運作。 歡迎您在[開發人員社群](https://developercommunity.visualstudio.com/spaces/41/index.html)針對任何議題提供意見反應。 未來將會有更多的變更！

Visual Studio Team Services (VSTS) 和 Team Foundation Server (TFS) 提供兩個模型的版本控制：Git 為分散式版本控制，Team Foundation 版本控制 (TFVC) 為集中式版本控制。 本文提供以 Visual Studio for Mac 使用 Team Foundation 版本控制的概觀和起始點。

## <a name="requirements"></a>需求

* Visual Studio for Mac 7.5 或更新版本。
* Visual Studio Team Services 或 Team Foundation Server 2013 和更新版本
* Visual Studio Team Services 或 Team Foundation Server 中的專案已設定為使用 Team Foundation 版本控制。

## <a name="installation"></a>安裝

在 Visual Studio for Mac 中，從功能表選擇 [Visual Studio] > [延伸模組...]。 在 [資源庫] 索引標籤中，選取 [版本控制] > [Team Foundation Version Control for TFS and VSTS] \(適用於 TFS 和 VSTS 的 Team Foundation 版本控制\)，然後按一下 [安裝...]：

  ![延伸模組管理員](media/tfvc-install.png) 

遵循提示安裝延伸模組。 安裝之後，重新啟動 IDE。

## <a name="using-the-add-in"></a>使用增益集

安裝延伸模組之後，選取 [版本控制] > [TFS/VSTS] > [連線至 Team Foundation 版本控制...] 功能表項目。 按一下 [新增] 新增新的帳戶： 

![新增 TFVC 伺服器](media/tfvc-add-remove-server.png)

請選擇 Visual Studio Team Services 或 Team Foundation Server 其中之一來開始：

![以 TFVC 服務器連線](media/tfvc-choose-server-type.png)

輸入您的認證，然後按一下 [登入]： 

![登入 TFVC 伺服器](media/tfvc-login.png)

成功登入之後，選取您要存取的專案，然後按下 [確定]： 

![選擇專案](media/tfvc-choose-projects.png)

選取 [版本控制] > [TFS/VSTS] > [原始檔控制總管] 功能表項目，以開啟 [原始檔控制總管] 讓您瀏覽原始檔。

> [!IMPORTANT]
> **已知問題**：在此預覽版本中，第一次開啟 [原始檔控制總管] 時，您必須先[建立新的工作區](#creating-a-new-workspace)。

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

按一下 [新增] 按鈕建立新的工作區。

![建立工作區](media/tfvc-create-workspace.png)

提供工作區的名稱，然後按一下 [新增工作資料夾] 以對應專案至您電腦上的本機資料夾。

完成之後，按一下 [確定]，然後關閉 [管理工作區] 對話方塊。 現在您可以透過 [原始程式碼總管] 取得檔案並開始使用。

## <a name="troubleshooting"></a>疑難排解

### <a name="problems-using-basic-authentication"></a>使用基本驗證的問題

您可以透過幾個不同的選項向伺服器執行驗證：

- OAuth
- 基本
- Ntlm

為了能夠使用基本驗證，您必須遵循下列步驟以在 VSTS 中啟用**替代驗證認證**：

1. 以帳戶擁有者身分登入您的 VSTS 帳戶 (https://{您的帳戶}.visualstudio.com)。
2. 從您的帳戶工具列，選取齒輪圖示，然後選取 [原則]：![選取 [原則] 設定選項](media/tfvc-auth2.png) 
3. 檢閱您的應用程式連線設定。 根據您的安全性原則來變更這些設定：![選取 [原則] 設定選項](media/tfvc-auth.png)  

### <a name="i-do-not-see-anything-in-tfvc"></a>我在 TFVC 中看不到任何項目

若要在您的開發電腦上設定 Team Foundation 版本控制 (TFVC)，您**必須**建立工作區，如[建立新的工作區](#creating-a-new-workspace)一節中所述。

在 [原始檔控制總管] 中，按下 [管理工作區] 按鈕。 請遵循步驟，將 Team 專案對應至開發電腦上的資料夾。

### <a name="i-do-not-see-any--all-of-my-projects"></a>我看不到自己的任何/所有專案

驗證之後，您應該會看到專案清單。 預設只會顯示 TFS 專案。 若要查看其他類型的專案，請勾選 [See all projects] \(查看所有專案\) 方塊。

請記住，如果您沒有正確的權限，則不會顯示位於伺服器以外位置的專案。

#### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>我收到錯誤：「無法建立工作區。 請重試」

嘗試[建立新的工作區](#creating-a-new-workspace)時，請務必符合下列條件：

- 工作區名稱中未使用無效的字元。
- 名稱必須少於 64 個字元。
- 任何其他工作區都不得使用本機路徑。