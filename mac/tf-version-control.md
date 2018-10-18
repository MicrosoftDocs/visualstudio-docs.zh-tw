---
title: Team Foundation Version Control (TFVC)
description: 使用 Team Foundation 版本控制 (TFVC) 連線到 Team Foundation Server 或 Azure DevOps Services。
author: conceptdev
ms.author: crdun
ms.date: 09/05/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 5a1d7fb7519e9402e2fa780e978fc1176702b26d
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542428"
---
# <a name="connecting-to-team-foundation-version-control"></a>連線到 Team Foundation 版本控制

> [!NOTE]
> **注意**：Team Foundation 版本控制支援目前為預覽版，某些功能尚無法完全運作。 歡迎您在[開發人員社群](https://developercommunity.visualstudio.com/spaces/41/index.html)針對任何議題提供意見反應。 未來將會有更多的變更！

Azure Repos 提供兩個模型的版本控制：Git 為分散式版本控制，Team Foundation 版本控制 (TFVC) 為集中式版本控制。 本文提供以 Visual Studio for Mac 使用 TFVC 的概觀和起始點。

## <a name="requirements"></a>需求

* Visual Studio Community、Professional 或 Enterprise for Mac 7.5 版或更新版本。
* Azure DevOps Services 或 Team Foundation Server 2013 和更新版本。
* Azure DevOps Services 或 Team Foundation Server 中的專案已設定為使用 Team Foundation 版本控制。

## <a name="installation"></a>安裝

在 Visual Studio for Mac 中，從功能表選擇 [Visual Studio] > [延伸模組...]。 在 [資源庫] 索引標籤中，選取 [版本控制] > [Team Foundation Version Control for TFS and VSTS] \(適用於 TFS 和 VSTS 的 Team Foundation 版本控制\)，然後按一下 [安裝...]：

  ![延伸模組管理員](media/tfvc-install.png)

遵循提示安裝延伸模組。 安裝之後，重新啟動 IDE。

## <a name="updating-the-extension"></a>更新延伸模組

TFVC 延伸模組的更新會定期進行。 若要存取更新，請從功能表中選擇 [Visual Studio] > [延伸模組...]，然後選取 [更新] 索引標籤。選取清單中的延伸模組，然後按 [更新] 按鈕：

  ![顯示更新的延伸模組管理員](media/tfvc-update.png)

在下一個對話方塊上按 [安裝]，以解除安裝舊套件並安裝新套件。

如需每個版本中新功能的資訊，請參閱[版本資訊](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-mac-preview-relnotes#team-foundation-version-control-extension--release-notes)。

## <a name="using-the-add-in"></a>使用增益集

安裝延伸模組之後，選取 [版本控制] > [TFS/Azure DevOps] > [從遠端存放庫開啟] 功能表項目。

  ![開啟延伸模組的功能表項目](media/tfvc-source-control-explorer-devops.png)

請選擇 VSTS 或 Team Foundation Server 其中之一來開始，並按 [繼續]：

  ![與伺服器連線](media/tfvc-choose-server-type-devops.png)

### <a name="azure-repos-authentication"></a>Azure Repos 驗證

當您選取 Azure Repos 上所裝載的專案時，系統會提示您輸入您的 Microsoft 帳戶詳細資料：

  ![與 Azure Repos 連線](media/tfvc-vsts-login.png)

### <a name="tfs-authentication"></a>TFS 驗證

若要連線至 TFS，請輸入伺服器詳細資料和您的帳戶認證。 輸入要使用 NTLM 驗證的網域，否則請保留空白以使用基本驗證。 選取 [新增伺服器]：

![登入 TFS 伺服器](media/tfvc-login.png)

## <a name="selecting-a-project"></a>選取專案

成功驗證之後，您可以在 [從原始檔控制開啟] 對話方塊中看到與帳戶建立關聯的存放庫清單：

  ![已顯示專案的 [從原始檔控制開始] 對話方塊](media/tfvc-vsts-projects.png)

這個對話方塊是以下列節點組織而成：

- Azure DevOps 組織或集合：這會顯示所有連線至您用以登入 Microsoft 帳戶的組織。
- 專案：在每個組織或集合中，您可以擁有數個專案。 專案是裝載原始程式碼、工作項目，以及自動化組建的位置。

此時，您可以透過專案或組織名稱進行搜尋和篩選。

### <a name="adding-a-new-server"></a>新增伺服器

若要將新的伺服器新增至清單中，請按 [從原始檔控制開啟] 對話方塊中的 [新增主機] 按鈕：

![醒目提示新增按鈕，將新的伺服器新增至清單](media/tfvc-add-new-server.png)

從清單中選取提供者，並輸入您的認證：

![顯示原始檔控制提供者選項的對話方塊](media/tfvc-add-new-creds-devops.png)

## <a name="creating-a-new-workspace"></a>新增新的工作區

若要開始使用專案，您必須具備「工作區」。 如果您還沒有工作區，則可以從 [從原始檔控制開啟] 對話方塊的 [工作區] 下拉式方塊中建立一個工作區：

![建立新的工作區下拉式方塊選項](media/tfvc-create-new-workspace.png)

設定新工作區的名稱和本機路徑，並選取 [建立工作區]：

![輸入新工作區的名稱和本機路徑](media/tfvc-local-workspace.png)

## <a name="using-the-source-code-explorer"></a>使用 [原始程式碼總管]

建立工作區並對應專案之後，您可以開始使用「原始程式碼總管」。

若要開啟 [原始程式碼總管]，請選取 [版本控制] > [TFS/Azure DevOps] > [原始檔控制總管] 功能表項目。

[原始程式碼總管] 可讓您巡覽所有對應的專案、其檔案及資料夾。 它也可讓您執行所有基本原始檔控制動作，例如：

- 取得最新版本
- 取得特定版本
- 存回和取出檔案
- 鎖定和解除鎖定檔案
- 新增、刪除和重新命名檔案
- 檢視記錄
- 比較變更。

其中的許多動作都可透過專案上的內容動作使用：

![專案的操作功能表動作](media/tfvc-sourcecode-actions.png)

## <a name="managing-workspaces"></a>管理工作區

如果您尚未依照[建立工作區](#creating-a-new-workspace)一節中所述來建立工作區，您會發現 [原始程式碼總管] 為空白：

![空白的 [原始程式碼總管]](media/tfvc-setup-empty-sce.png)

若要設定使用本機工作區的遠端專案，請使用下列步驟：

1. 從下拉式方塊中選取 [伺服器]。
1. 請注意，目前「沒有工作區」，且本機路徑是「未對應」。 選取 [未對應] 連結，以顯示 [建立新的工作區] 對話方塊。
1. 提供工作區的名稱，然後按一下 [新增工作資料夾] 將專案對應至您電腦上的本機資料夾：

    ![顯示預設選項的 [建立新的工作區] 對話方塊](media/tfvc-workspace1.png)

1. 選取 "$" 資料夾，將您伺服器上所有專案都對應至相同的工作區，或選取個別的專案，然後按一下 [確定]：

    ![瀏覽顯示所有專案的資料夾對話方塊](media/tfvc-workspace2.png)

1. 選取本機電腦上專案對應目標的位置，然後按一下 [選取資料夾]。
1. 按 [確定] 以確認新工作區的詳細資料

    ![已新增工作資料夾的 [建立新的工作區] 對話方塊](media/tfvc-workspace3.png)

設定您的工作區之後，透過按一下 [原始程式碼總管] 中的 [管理工作區] 按鈕，即可加以變更或移除。

![管理工作區](media/tfvc-workspace4.png)

## <a name="troubleshooting"></a>疑難排解

### <a name="problems-using-basic-authentication"></a>使用基本驗證的問題

下列選項可用來向伺服器進行驗證：

- OAuth
- 基本
- Ntlm

為了使用基本驗證，您必須遵循下列步驟以在 Azure DevOps Services 中啟用**替代驗證認證**：

1. 以擁有者身分登入您的 Azure DevOps 組織 (https://dev.azure.com/{organization}/{project})。

2. 從您的組織工具列選取齒輪圖示，然後選取 [原則]：

    ![已選取 [原則] 設定選項](media/tfvc-auth2.png)

3. 檢閱您的應用程式連線設定。 根據您的安全性原則來變更這些設定：

    ![已選取 [原則] 設定選項](media/tfvc-auth.png)

### <a name="i-do-not-see-anything-in-tfvc"></a>我在 TFVC 中看不到任何項目

若要在您的開發電腦上設定 Team Foundation 版本控制 (TFVC)，您**必須**建立工作區，如[管理工作區](#managing-workspaces)一節中所述。

在 [原始檔控制總管] 中，按下 [管理工作區] 按鈕。 請遵循步驟，將專案對應至開發電腦上的資料夾。

### <a name="i-do-not-see-any--all-of-my-projects"></a>我看不到自己的任何/所有專案

驗證之後，您應該會看到專案清單。 根據預設，只會顯示 TFS 專案。 若要查看其他類型的專案，請勾選 [See all projects] \(查看所有專案\) 方塊。

請記住，如果您沒有正確的權限，則不會顯示位於伺服器以外位置的專案。

#### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>我收到錯誤：「無法建立工作區。 請重試」

嘗試[建立新的工作區](#creating-a-new-workspace)時，請務必符合下列條件：

- 工作區名稱中未使用無效的字元。
- 名稱必須少於 64 個字元。
- 任何其他工作區都不得使用本機路徑。