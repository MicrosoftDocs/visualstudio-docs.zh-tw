---
title: Team Foundation Version Control (TFVC)
description: 關於 TFVC 與 macOS 的疑難排解。
author: jmatthiesen
ms.author: jomatthi
ms.date: 09/02/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.topic: troubleshooting
ms.openlocfilehash: 11b0788317cd0a20dd27159aa241db32e3818daf
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722122"
---
# <a name="does-visual-studio-for-mac-support-team-foundation-version-control"></a>Visual Studio for Mac 是否支援 Team Foundation 版本控制？

> [!CAUTION]
> Visual Studio 2019 for Mac 已不再支援 Visual Studio for Mac 的 TFVC 延伸模組預覽版本。


## <a name="alternative-version-control-options-in-visual-studio-for-mac"></a>Visual Studio for Mac 中的替代版本控制選項

為了獲得最佳的 macOS 版本控制體驗，我們建議使用 **Git** ，而不是 TEAM FOUNDATION 版本控制 (TFVC) 。 

Visual Studio for Mac 支援 Git，它是 Team Foundation Server (TFS)/Azure DevOps 中裝載之存放庫的預設選項。 若要深入了解有關搭配 TFS/Azure DevOps 使用 Git 的詳細資訊，請參閱[設定 Git 存放庫](./set-up-git-repository.md)指南。

## <a name="unsupported-workarounds-for-tfvc"></a>不支援的 TFVC 因應措施

雖然 Visual Studio for Mac 為正式支援 TFVC，但此指南的剩餘部分提供在 macOS 上使用 TFVC 的一些因應措施。 如果您今天使用 TFVC 進行版本控制，可以使用以下解決方案來存取 TFVC 中裝載的原始程式碼：

* 選項 1。 [ 針對圖形化 UI 使用 Visual Studio Code 和 Azure Repos 擴充功能](#use-visual-studio-code-and-the-azure-repos-extension)
* 選項 2。 [使用 Team Explorer Everywhere 命令列用戶端 (TEE-CLC) 連線到您的存放庫](#connecting-using-the-team-explorer-everywhere-command-line-client)

### <a name="option-1--use-visual-studio-code-and-the-azure-repos-extension"></a>選項 1。 <a id="use-visual-studio-code-and-the-azure-repos-extension"></a> 使用 Visual Studio Code 和 Azure Repos 擴充功能

如果您希望使用圖形化介面來管理版本控制中的檔案，則 Visual Studio Code 的 Azure Repos 延伸模組可提供由 Microsoft 支援的解決方案。 若要開始使用，請下載 [Visual Studio Code](https://code.visualstudio.com)，然後了解如何[設定 Azure Repos 延伸模組](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team)。

### <a name="option-2--connecting-using-the-team-explorer-everywhere-command-line-client"></a>選項 2。 <a id="connecting-using-the-team-explorer-everywhere-command-line-client"></a> 使用 Team Explorer Everywhere 命令列用戶端連接

> [!IMPORTANT]
> 作為 Team Explorer Everywhere README 的一部分，我們已[不再維護此專案](https://github.com/microsoft/team-explorer-everywhere)。

如果您習慣使用 macOS 終端機，那麼 Team Explorer Everywhere 命令列用戶端 (TEE CLC) 會提供支援的方法，來連線到您在 TFVC 中的來源。

您可以遵循下列步驟來設定與 TFVC 的連線並認可變更。

#### <a name="setting-up-the-tee-clc"></a>設定 TEE-CLC

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

#### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>使用 TEE-CLC 連線到您的存放庫

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

#### <a name="committing-changes-using-the-tee-clc"></a>使用 TEE-CLC 認可變更

在 Visual Studio for Mac 中對檔案進行變更後，可以切換回終端機以簽入編輯內容。 `tf add` 命令用於將檔案新增至要簽入的暫止變更清單中，而 `tf checkin` 命令執行對伺服器的實際簽入。 `checkin` 命令包括用於新增註解或產生相關工作項目關聯的參數。 在下列程式碼片段中，`WebApp.Services` 資料夾中的所有檔案將以遞迴方式新增到簽入中。 然後，使用註解簽入程式碼，並將其與識別碼為 "42"　的工作項目相關聯。

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

若要深入了解有關此處所述的命令或其他命令的詳細資訊，您可以從終端機使用下列命令：

`tf help`

## <a name="see-also"></a>另請參閱

- [使用 Visual Studio 在 TFVC 中開發和共用您的程式碼 (Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)