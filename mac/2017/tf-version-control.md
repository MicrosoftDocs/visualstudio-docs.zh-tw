---
title: Team Foundation Version Control (TFVC)
description: 使用 Team Foundation 版本控制 (TFVC) 從 Visual Studio for Mac 連線到 Team Foundation Server/Azure DevOps。
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/25/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.topic: troubleshooting
ms.openlocfilehash: b9aa9b718ad4618502a58185c27333d689c74300
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729375"
---
# <a name="connecting-to-team-foundation-version-control"></a>連線到 Team Foundation 版本控制

> [!NOTE]
> 為了獲得最佳的 macOS 版本控制體驗，我們建議使用 Git 而不是 Team Foundation 版本控制 (TFVC)。 Visual Studio for Mac 支援 Git，它是 Team Foundation Server (TFS)/Azure DevOps 中裝載之存放庫的預設選項。 若要深入了解有關將 Git 與 TFS/Azure DevOps 一起使用的詳細資訊，請參閱[設定 Git 存放庫](./set-up-git-repository.md)一文。
>
> 如果您之前使用的是 Visual Studio for Mac 的 TFVC 延伸模組預覽版本，當您升級至 Visual Studio 2019 for Mac 後即不再支援。

Azure Repos 提供兩種版本控制模型： [Git](/azure/devops/repos/git/?view=azure-devops&preserve-view=true)、分散式版本控制系統，以及 [Team Foundation 版本控制](/azure/devops/repos/tfvc/index?view=azure-devops&preserve-view=true) (TFVC) ，也就是集中式版本控制系統。

Visual Studio for Mac 提供對 Git 存放庫的完整支援，但需要一些的因應措施才能使用 TFVC。 如果您今天使用 TFVC 進行版本控制，可以使用以下解決方案來存取 TFVC 中裝載的原始程式碼：

* [針對圖形化使用者介面使用 Visual Studio Code 和 Azure Repos 延伸模組](#use-visual-studio-code-and-the-azure-repos-extension)
* [使用 Team Explorer Everywhere 命令列用戶端 (TEE-CLC) 連線到您的存放庫](#connecting-using-the-team-explorer-everywhere-command-line-client)
* [使用適用於 Visual Studio for Mac 的Team Foundation 版本控制延伸模組 (不支援) 連線到 TFVC](#connect-to-tfvc-using-the-team-foundation-version-control-extension)

本文的其餘部分會向您逐步介紹以上所列的選項。

## <a name="requirements"></a>規格需求

* Visual Studio Community、Professional 或 Enterprise for Mac 7.8 版及更新版本。
* Azure DevOps Services、Team Foundation Server 2013 及更新版本，或 Azure DevOps Server 2018 及更新版本。
* Azure DevOps Services 或 Team Foundation Server/Azure DevOps Server 中的專案已設定為使用 Team Foundation 版本控制。

## <a name="use-visual-studio-code-and-the-azure-repos-extension"></a>使用 Visual Studio Code 和 Azure Repos 延伸模組

如果您希望使用圖形化介面來管理版本控制中的檔案，則 Visual Studio Code 的 Azure Repos 延伸模組可提供由 Microsoft 支援的解決方案。 若要開始使用，請下載 [Visual Studio Code](https://code.visualstudio.com)，然後了解如何[設定 Azure Repos 延伸模組](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team)。

## <a name="connecting-using-the-team-explorer-everywhere-command-line-client"></a>使用 Team Explorer Everywhere 命令列用戶端進行連線

如果您習慣使用 macOS 終端機，那麼 Team Explorer Everywhere 命令列用戶端 (TEE CLC) 會提供支援的方法，來連線到您在 TFVC 中的來源。

您可以遵循下列步驟來設定與 TFVC 的連線並認可變更。

### <a name="setting-up-the-tee-clc"></a>設定 TEE-CLC

有兩種方法可以使用 TEE-CLC 進行安裝。

* 使用 Homebrew 安裝用戶端，或
* 下載並手動安裝用戶端

最簡單的解決方案是 **使用 HomeBrew**，這是適用於 macOS 的套件管理員。 若要使用此方法進行安裝：

1. 啟動 macOS 終端機應用程式。
1. 使用終端機和 [Homebrew 首頁](https://brew.sh/)上的說明安裝 Homebrew。
1. 安裝 Homebrew 之後，請從您的終端機執行下列命令：`brew install tee-clc`

**手動設定 TEE CLC**：

1. 從 Team Explorer Everywhere GitHub 儲存機制的 [版本] 頁面[下載最新版本的 tee-clc](https://github.com/Microsoft/team-explorer-everywhere/releases) (例如撰寫本文時的 tee-clc-14.134.0.zip)。
1. 將 .zip 的內容解壓縮到磁碟上的資料夾。
1. 開啟 macOS 終端機應用程式，並使用 `cd` 命令切換至您在上一個步驟中使用的資料夾。
1. 在資料夾中，執行命令 `./tf` 以測試是否可以執行命令列用戶端，系統可能會提示您安裝 Java 或其他相依性。

安裝 TEE-CLC 之後，您可以執行命令 `tf eula` 來檢視並接受用戶端的授權合約。

最後，若要使用 TFS/Azure DevOps 環境進行驗證，您需要在伺服器上建立個人存取權杖。 深入了解[使用個人存取權杖進行驗證](/azure/devops/integrate/get-started/authentication/pats?view=azure-devops&preserve-view=true)。 建立用於 TFVC 的個人存取權杖時，請確保在設定權杖時提供完整的存取權。

### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>使用 TEE-CLC 連線到您的存放庫

若要連線到您的原始程式碼，首先需要使用 `tf workspace` 命令建立工作區。 例如，下列命令會連線到名為 "MyOrganization" 的 Azure DevOps Services 中的組織： 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

`TF_AUTO_SAVE_CREDENTIALS` 環境設定用來儲存您的認證，因此系統不會提示您輸入多次認證。 當系統提示輸入使用者名稱時，請使用您在上一節中建立的個人存取權杖並使用空白密碼。

若要建立來源檔案到本機資料夾的對應，您將使用 `tf workfold` 命令。 下列範例會對應 "MyRepository" TFVC 專案中名為 "WebApp.Services" 的資料夾，並將它設定為複製到本機 ~/Projects/ 資料夾中 (例如，目前使用者主資料夾中的 "Projects" 資料夾)。

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

最後，使用下列命令從伺服器取得來源檔案，並將其複製到本機：

```bash
tf get
```

### <a name="committing-changes-using-the-tee-clc"></a>使用 TEE-CLC 認可變更

在 Visual Studio for Mac 中對檔案進行變更後，可以切換回終端機以簽入編輯內容。 `tf add` 命令用於將檔案新增至要簽入的暫止變更清單中，而 `tf checkin` 命令執行對伺服器的實際簽入。 `checkin` 命令包括用於新增註解或產生相關工作項目關聯的參數。 在下列程式碼片段中，`WebApp.Services` 資料夾中的所有檔案將以遞迴方式新增到簽入中。 然後，使用註解簽入程式碼，並將其與識別碼為 "42"　的工作項目相關聯。

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

若要深入了解有關此處所述的命令或其他命令的詳細資訊，您可以從終端機使用下列命令：

`tf help`

## <a name="connect-to-tfvc-using-the-team-foundation-version-control-extension"></a>使用 Team Foundation 版本控制延伸模組連線到 TFVC

> [!NOTE]
> 為了獲得最佳的 macOS 版本控制體驗，我們建議使用 Git 而不是 Team Foundation 版本控制 (TFVC)。 Visual Studio for Mac 支援 Git，它是 Team Foundation Server (TFS)/Azure DevOps 中裝載之存放庫的預設選項。 若要深入了解有關將 Git 與 TFS/Azure DevOps 一起使用的詳細資訊，請參閱[設定 Git 存放庫](./set-up-git-repository.md)一文。
>
> 如果您之前使用的是 Visual Studio for Mac 的 TFVC 延伸模組預覽版本，當您升級至 Visual Studio 2019 for Mac 後即不再支援。

在 Visual Studio for Mac 延伸模組資源庫中，有一個 Team Foundation 版本控制延伸模組，為連線到 TFVC 提供有限的支援。 不支援該延伸模組且存在數個已知的問題，因此使用時您的體驗可能會有所不同。

若要安裝延伸模組，請啟動 Visual Studio for Mac 並選擇 [Visual Studio] > [延伸模組] 功能表。 在 [資源庫] 索引標籤中，選取 [版本控制] > [適用於 TFS 和 Azure DevOps 的 Team Foundation 版本控制]，然後按一下 [安裝]：

![延伸模組管理員](media/tfvc-install.png)

遵循提示安裝延伸模組。 安裝之後，重新啟動 IDE。

### <a name="updating-the-extension"></a>更新延伸模組

TFVC 延伸模組的更新會定期進行。 若要存取更新，請從功能表中選擇 [ **Visual Studio > 擴充功能 ...** ]，然後選取 [ **更新** ] 索引標籤。選取清單中的延伸模組，然後按下 [ **更新** ] 按鈕：

在下一個對話方塊上按 [安裝]，以解除安裝舊套件並安裝新套件。

### <a name="using-the-extension"></a>使用延伸模組

安裝延伸模組之後，選取 [版本控制] > [TFS/Azure DevOps] > [從遠端存放庫開啟] 功能表項目。

![開啟延伸模組的功能表項目](media/tfvc-source-control-explorer-devops.png)

請選擇 VSTS 或 Team Foundation Server 其中之一來開始，並按 [繼續]：

![與伺服器連線](media/tfvc-choose-server-type-devops.png)

#### <a name="azure-repos-authentication"></a>Azure Repos 驗證

當您選取 Azure Repos 上所裝載的專案時，系統會提示您輸入您的 Microsoft 帳戶詳細資料：

![與 Azure Repos 連線](media/tfvc-vsts-login.png)

#### <a name="tfs-authentication"></a>TFS 驗證

若要連線至 TFS，請輸入伺服器詳細資料和您的帳戶認證。 輸入要使用 NTLM 驗證的網域，否則請保留空白以使用基本驗證。 選取 [新增伺服器]：

![登入 TFS 伺服器](media/tfvc-login.png)

### <a name="selecting-a-project"></a>選取專案

成功驗證之後，您可以在 [從原始檔控制開啟] 對話方塊中看到與帳戶建立關聯的存放庫清單：

![已顯示專案的 [從原始檔控制開始] 對話方塊](media/tfvc-vsts-projects.png)

這個對話方塊是以下列節點組織而成：

- Azure DevOps 組織或集合：這會顯示所有連線至您用以登入 Microsoft 帳戶的組織。
- 專案：在每個組織或集合中，您可以擁有數個專案。 專案是裝載原始程式碼、工作項目，以及自動化組建的位置。

此時，您可以透過專案或組織名稱進行搜尋和篩選。

#### <a name="adding-a-new-server"></a>新增伺服器

若要將新的伺服器新增至清單中，請按 [從原始檔控制開啟] 對話方塊中的 [新增主機] 按鈕：

![醒目提示新增按鈕，將新的伺服器新增至清單](media/tfvc-add-new-server.png)

從清單中選取提供者，並輸入您的認證：

![顯示原始檔控制提供者選項的對話方塊](media/tfvc-add-new-creds-devops.png)

### <a name="creating-a-new-workspace"></a>新增新的工作區

若要開始使用專案，您必須具備「工作區」。 如果您還沒有工作區，則可以從 [從原始檔控制開啟] 對話方塊的 [工作區] 下拉式方塊中建立一個工作區：

![建立新的工作區下拉式方塊選項](media/tfvc-create-new-workspace.png)

設定新工作區的名稱和本機路徑，並選取 [建立工作區]：

![輸入新工作區的名稱和本機路徑](media/tfvc-local-workspace.png)

### <a name="using-the-source-code-explorer"></a>使用 [原始程式碼總管]

建立工作區並對應專案之後，您可以開始使用「原始程式碼總管」。

若要開啟 [原始程式碼總管]，請選取 [版本控制] > [TFS/Azure DevOps] > [原始檔控制總管] 功能表項目。

[原始程式碼總管] 可讓您巡覽所有對應的專案、其檔案及資料夾。 它也可讓您執行所有基本原始檔控制動作，例如：

- 取得最新版本
- 取得特定版本
- 存回和取出檔案
- 鎖定和解除鎖定檔案
- 新增、刪除和重新命名檔案
- 檢視歷程記錄
- 比較變更。

其中的許多動作都可透過專案上的內容動作使用：

![專案的操作功能表動作](media/tfvc-sourcecode-actions.png)

### <a name="managing-workspaces"></a>管理工作區

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

## <a name="troubleshooting-and-known-issues"></a>疑難排解和已知問題

#### <a name="problems-using-basic-authentication"></a>使用基本驗證的問題

下列選項可用來向伺服器進行驗證：

- OAuth
- Basic
- Ntlm

為了使用基本驗證，您必須遵循下列步驟以在 Azure DevOps Services 中啟用 **替代驗證認證**：

1. 以擁有者的身分，登入您的 Azure DevOps 組織 (https:\//dev.azure.com/{organization}/{project})。

2. 從您的組織工具列選取齒輪圖示，然後選取 [原則]：

    ![已選取齒輪圖示的 Azure DevOps 組織工具列的螢幕擷取畫面，以及在下拉式功能表中選取的原則。](media/tfvc-auth2.png)

3. 檢閱您的應用程式連線設定。 根據您的安全性原則來變更這些設定：

    ![[Azure DevOps Services] 中 [原則] 畫面的螢幕擷取畫面，其中顯示應用程式連接原則的設定。](media/tfvc-auth.png)

#### <a name="i-do-not-see-anything-in-tfvc"></a>我在 TFVC 中看不到任何項目

若要在您的開發電腦上設定 Team Foundation 版本控制 (TFVC)，您 **必須** 建立工作區，如 [管理工作區](#managing-workspaces)一節中所述。

在 [原始檔控制總管] 中，按下 [管理工作區] 按鈕。 請遵循步驟，將專案對應至開發電腦上的資料夾。

#### <a name="i-do-not-see-any--all-of-my-projects"></a>我看不到自己的任何/所有專案

驗證之後，您應該會看到專案清單。 根據預設，只會顯示 TFS 專案。 若要查看其他類型的專案，請勾選 [See all projects] \(查看所有專案\) 方塊。

請記住，如果您沒有正確的權限，則不會顯示位於伺服器以外位置的專案。

##### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>我收到錯誤：「無法建立工作區。 請重試」

嘗試[建立新的工作區](#creating-a-new-workspace)時，請務必符合下列條件：

- 工作區名稱中未使用無效的字元。
- 名稱必須少於 64 個字元。
- 任何其他工作區都不得使用本機路徑。

### <a name="see-also"></a>請參閱

- [使用 Visual Studio 在 TFVC 中開發和共用您的程式碼 (Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)