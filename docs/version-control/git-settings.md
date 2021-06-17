---
title: Visual Studio 中的 Git 設定
titleSuffix: ''
description: 瞭解 Visual Studio 如何使用 .gitconfig 儲存檔案和 Git 設定來管理您的喜好設定
ms.date: 06/08/2021
ms.topic: conceptual
ms.author: prnadago
author: prnadago
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.manager: jmartens
monikerRange: '>=vs-2019'
ms.openlocfilehash: f8dd9781833706a73b82a71236d42cc71c9fb9ec
ms.sourcegitcommit: 113b7df611583307d3965984233a33355d6b0318
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/16/2021
ms.locfileid: "112126621"
---
# <a name="git-settings-and-preferences-in-visual-studio"></a>Visual Studio 中的 Git 設定和喜好設定

在 Visual Studio 中，您可以設定和查看一般 Git 設定和喜好設定，例如您的名稱和電子郵件地址、慣用的差異和合併工具等等。 您可以在 [ **Git 全域設定**] 頁面上的 [**選項] 對話方塊** 中，查看並設定這些設定和喜好設定， (套用至所有存放庫) 或 **git 存放庫設定** 頁面 (適用于目前的儲存機制) 。

您可以設定兩種類型的設定：

- [Git 設定](#git-settings) -此區段中的設定對應至 git 設定檔中儲存的 git 設定。 這些設定可以在 Visual Studio 中查看及修改，但會由 Git 設定檔管理。
- [Visual Studio 設定](#visual-studio-settings) -本節中的設定會設定由 Visual Studio 管理的 Git 相關設定和喜好設定。

## <a name="how-to-configure-settings"></a>如何設定設定

1. 若要在 Visual Studio 中設定 Git 設定，請從最上層 Git 功能表選擇 [ **設定** ]。

   :::image type="content" source="media/git-menu-settings.png" alt-text="具有 [設定] 命令之注標的 Git 功能表。":::

2. 選擇 [ **Git 全域設定** ] 或 [ **Git 存放庫設定** ]，以查看及設定全域層級或存放庫層級的設定。

   :::image type="content" source="media/source-control-settings.png" alt-text="[選項] 對話方塊中的 [流覽] 窗格，其中包含 Git 設定的標注。":::

3. 您可以設定數個常見的 Git 設定，如本文的下列各節所述。 設定您想要的設定之後，請選取 **[確定]** 以儲存更新的設定。

   :::image type="content" source="media/ok-button.png" alt-text="[選項] 對話方塊的顯示區域，其中包含 [確定] 按鈕的標注。":::

## <a name="git-settings"></a>Git 設定

您也可以設定及檢查一些最常見的 Git 設定。 您可以在 Visual Studio 中查看和修改下列設定，即使它們是由 Git 設定檔所管理也一樣。

- [名稱和電子郵件](#name-and-email)
- [提取時剪除遠端分支](#prune-remote-branches-during-fetch)
- [提取時將本機分支重定基底](#rebase-local-branch-when-pulling)
- [密碼編譯網路提供者](#cryptographic-network-provider)
- [認證協助程式](#credential-helper)
- [差異 & 合併工具](#diff--merge-tools)
- [Git 檔案](#git-files)
- [遙控器](#remotes)
- 「其他設定」

>[!NOTE]
>在 Visual Studio 的 **全域設定** 中設定的 git 設定會對應到 git 使用者專屬設定檔中的設定，而存放 **庫設定** 中的設定會對應到存放庫特定設定檔中的設定。 如需 Git 設定的詳細資訊，請參閱《 Pro Git 》中有關 [自訂 git 的章節](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration)、 [git 配置](https://git-scm.com/docs/git-config)檔，以及 [設定檔上的 pro git 參考](https://git-scm.com/docs/git-config#FILES)。 若要設定 Visual Studio 中未公開的 Git 設定，請使用 `git config` 命令將值寫入設定檔： `git config [--local|--global|--system] section.key value` 。

### <a name="name-and-email"></a>名稱和電子郵件

您提供的名稱和電子郵件將用來作為您所進行之任何認可的認可者資訊。 這項設定適用于全域和儲存機制範圍，且會對應至 `git config` [user.name](https://git-scm.com/docs/git-config#Documentation/git-config.txt-username) 和 [user.email](https://git-scm.com/docs/git-config#Documentation/git-config.txt-useremail) 設定。

1. 從 Git 功能表中，移至 [ **設定**]。 若要在全域層級設定您的使用者名稱和電子郵件，請移至 **Git 全域設定**;若要在存放庫層級設定您的使用者名稱和電子郵件，請移至 **Git 存放庫設定**。

2. 提供您的使用者名稱和電子郵件，然後選擇 **[確定]** 以儲存。 

   :::image type="content" source="media/user-email-setting.png" alt-text="[選項] 對話方塊中的 [Git 全域設定] 窗格，其中包含將電子郵件設為使用者名稱的標注。":::

### <a name="prune-remote-branches-during-fetch"></a>提取時剪除遠端分支

剪除會移除遠端追蹤分支，這些分支不再存在於遠端，並可協助您讓您的分支清單保持乾淨和最新狀態。 這項設定適用于全域和儲存機制範圍，且會對應至 `git config` [fetch](https://git-scm.com/docs/git-config#Documentation/git-config.txt-fetchprune) 設定。

建議您在全域層級將此選項設定為 **True** 。 有效的設定為，如下所示：

- True (建議的) 
- False
- 取消設定 (預設) 

1. 從 Git 功能表中，移至 [ **設定**]。 移至 **Git 全域設定** ，在全域層級設定此選項;移至 **git 存放庫設定** ，以在存放庫層級設定此選項。

2. 將 **fetch 中** 的「剪除遠端分支」設為 **True** (建議的) 。 選取 **[確定]** 以儲存。

:::image type="content" source="media/prune-setting.png" alt-text="顯示 [提取期間剪除遠端分支] 的螢幕擷取畫面，並已從下拉式清單中選取 [True]。":::    

### <a name="rebase-local-branch-when-pulling"></a>提取時將本機分支重定基底

重定基底會將目前分支中不在上游分支內的認可所做的變更，重設為上游分支的最新分支，然後套用先前設定的變更。 這項設定可同時在全域和儲存機制範圍中使用，並且對應至 [ `git config` [拉重基](https://git-scm.com/docs/git-config#Documentation/git-config.txt-pullrebase) 底] 設定。 有效的設定為，如下所示：

- True：在提取之後，將目前的分支與上游分支的最上層進行基底。
- False：將目前的分支合併至上游分支。
- 取消設定 (預設) ：除非在其他設定檔中指定，否則請將最新分支合併至上游分支。
- 互動式：互動模式中的重定基底。
- 保留：若未在本機建立的合併認可進行重訂基底。

1. 從 Git 功能表中，移至 [ **設定**]。 移至 **Git 全域設定** ，在全域層級設定此選項;移至 **git 存放庫設定** ，以在存放庫層級設定此選項。

2. 當您提取至所需的設定時，請設定重定 **基底本機分支** ，然後選取 **[確定]** 以儲存。

    :::image type="content" source="media/rebase-setting.png" alt-text="顯示反白顯示 [從下拉式清單中移除時，將本機分支重定基底] 的螢幕擷取畫面，並從下拉式清單選取 [True]。":::

`pull.rebase`在 Visual Studio 中無法設定為 **互動式**。 Visual Studio 沒有互動式重定基底支援。
若要設定 `pull.rebase` 為使用互動模式，請使用命令列。

### <a name="cryptographic-network-provider"></a>密碼編譯網路提供者

密碼編譯網路提供者是全域範圍的 Git 設定設定，可設定在執行時間使用的 TLS/SSL 後端，以及對應至 `git config` [sslBackend](https://git-scm.com/docs/git-config#Documentation/git-config.txt-httpsslBackend) 設定。 這些值如下：

- OpenSSL：針對 TLS 和 SSL 通訊協定使用 [OpenSSL](https://www.openssl.org/) 。
- 安全通道：針對 TLS 和 SSL 通訊協定使用 [安全通道 (schannel) ](/windows/win32/secauthn/secure-channel) 。 Schannel 是原生 Windows 解決方案，存取 Windows 認證存放區，因此可讓您進行全企業的憑證管理。
- 取消設定 (預設) ：如果未設定此設定，則預設值為 OpenSSL。

1. 從 Git 功能表中，移至 [ **設定**]。 移至 [ **Git 全域設定** ] 以設定此設定。

2. 將 **密碼編譯網路提供者** 設定為所需的值，然後選取 **[確定]** 以儲存。

   :::image type="content" source="media/network-provider-setting.png" alt-text="顯示 [密碼編譯網路提供者] 的螢幕擷取畫面，其中已從下拉式清單中選取 [OpenSSL] 反白顯示。":::

### <a name="credential-helper"></a>認證協助程式

當 Visual Studio 執行遠端 Git 操作時，遠端端點可能會拒絕要求，因為要求需要提供認證。 屆時，Git 會叫用認證協助程式，這會傳回執行作業所需的認證，然後再次嘗試要求。 使用的認證協助程式會對應至 `git config` [credential. helper](https://git-scm.com/docs/gitcredentials) 設定。 您可以在全域範圍中使用下列值：

- 適用于 Windows 的 GCM：使用 [Git 認證管理員 For windows](https://github.com/microsoft/Git-Credential-Manager-for-Windows) 作為 helper。
- GCM 核心：使用 [Git 認證管理員 Core](https://github.com/microsoft/Git-Credential-Manager-Core) 作為 helper。
- 取消設定 (預設) ：如果未設定此設定，則會使用系統設定中設定的認證協助程式。 從 Git for Windows 2.29，預設認證協助程式是 GCM Core。

1. 從 Git 功能表中，移至 [ **設定**]。 移至 [ **Git 全域設定** ] 以設定此設定。

2. 將 **認證 helper** 設定為所需的值，然後選取 **[確定]** 儲存。

:::image type="content" source="media/credential-helper-setting.png" alt-text="顯示 [選項] 對話方塊中 [認證協助程式] 設定的螢幕擷取畫面。":::

### <a name="diff--merge-tools"></a>差異 & 合併工具

Git 會在您慣用的工具中顯示差異和合併衝突。 此區段中的設定會對應到 [ `git config` [diff] 工具](https://git-scm.com/docs/git-config#Documentation/git-config.txt-difftool) 和 [ [合併] 工具](https://git-scm.com/docs/git-config#Documentation/git-config.txt-mergetool) 設定。 您可以選取 [**使用 Visual Studio**]，將 git 設定為使用 Visual Studio 作為 **Git 全域設定** 和 **git 存放庫設定** 中的合併或差異工具。 若要設定其他 diff 和合併工具，請使用 `git config` with [diff. tool](https://git-scm.com/docs/git-config#Documentation/git-config.txt-difftool) 或 [merge. tool](https://git-scm.com/docs/git-config#Documentation/git-config.txt-mergetool) 參數。

:::image type="content" source="media/tools-setting.png" alt-text="顯示在 [選項] 對話方塊中設定 [預設差異] 工具和 [合併] 工具區段的螢幕擷取畫面。":::

### <a name="git-files"></a>Git 檔案

您可以使用 **git 存放庫設定** 範圍中的 **git** 檔案區段，來查看和編輯存放庫的 [.gitignore](https://git-scm.com/docs/gitignore)和 [>.gitattributes](https://git-scm.com/docs/gitattributes)檔案。

:::image type="content" source="media/git-files-setting.png" alt-text="螢幕擷取畫面，顯示在您的存放庫中，用來查看和編輯忽略和屬性檔案的區段。":::

### <a name="remotes"></a>遙控器

您可以使用 [ **Git 存放庫設定**] 下的 [**遠端**] 窗格來設定存放庫的遠端。 此設定對應于 [git 遠端](https://git-scm.com/docs/git-remote) 命令，可讓您新增、編輯或移除遠端。

:::image type="content" source="media/remotes-settings.png" alt-text="螢幕擷取畫面，顯示 [選項] 對話方塊中的 [Git 遠端] 窗格。":::

### <a name="other-settings"></a>其他設定

若要查看所有其他 Git 設定，您可以開啟和查看設定檔案，也可以執行 `git config --list` 以顯示設定。

## <a name="visual-studio-settings"></a>Visual Studio 設定

下列設定可管理 Visual Studio 中的 Git 相關喜好設定，並由 Visual Studio 管理，而不是 Git 設定檔。 此區段中的所有設定都是在 [ **Git 全域設定** ] 頁面中設定。

- [預設位置](#default-location)
- [開啟存放庫時關閉未在 Git 下開啟的解決方案](#close-open-solutions-not-under-git-when-opening-a-repository)
- [啟用從協力廠商來源下載作者影像](#enable-download-of-author-images-from-third-party-sources)
- [依預設在合併後認可變更](#commit-changes-after-merge-by-default)
- [啟用 push--force](#enable-push---force-with-lease)
- [開啟 Git 存放庫時，在方案總管中開啟資料夾](#open-folder-in-solution-explorer-when-opening-a-git-repository)
- [開啟 Git 存放庫時自動載入解決方案](#automatically-load-the-solution-when-opening-a-git-repository)
- [按兩下或按 Enter 鍵來自動簽出分支](#automatically-check-out-branches-with-double-click-or-the-enter-key)

### <a name="default-location"></a>預設位置

**預設位置** 會設定要在其中複製存放庫的預設資料夾。

:::image type="content" source="media/default-location-setting.png" alt-text="顯示 [選項] 對話方塊中 [預設位置] 欄位的螢幕擷取畫面。":::

### <a name="close-open-solutions-not-under-git-when-opening-a-repository"></a>開啟存放庫時關閉未在 Git 下開啟的解決方案

依預設，當您切換到另一個存放庫時，Visual Studio 會關閉任何開啟的方案或資料夾。 當它執行這項操作時，也可能會根據您在開啟 [git 存放庫時，選擇在方案總管中開啟資料夾](#open-folder-in-solution-explorer-when-opening-a-git-repository) ，並在開啟 git 存放庫 [時自動載入解決方案](#automatically-load-the-solution-when-opening-a-git-repository)，來載入新儲存機制的解決方案或資料夾。 這會維護開啟的程式碼與開啟的儲存機制之間的一致性。 但是，如果您的解決方案與您的儲存機制不在相同的資料夾根目錄中，您可能會想要在切換至其儲存機制時，讓解決方案保持開啟狀態。 您可以使用此設定來這麼做。 這些值如下：

- 是：開啟存放庫時，一律會關閉目前開啟的解決方案
- 否：開啟存放庫時，Visual Studio 會檢查目前的解決方案是否在 Git 下。 如果不是，則解決方案會保持開啟。
- 一律詢問 (預設) ：當設定此選項時，不論您要讓目前的解決方案保持開啟或關閉，您都可以透過每個儲存機制開啟的對話方塊來進行選擇。

:::image type="content" source="media/close-sln-setting.png" alt-text="顯示 [選項] 對話方塊中 [關閉方案] 設定的螢幕擷取畫面。":::


### <a name="enable-download-of-author-images-from-third-party-sources"></a>啟用從協力廠商來源下載作者影像

啟用從協力廠商來源下載作者映射是在全域範圍 Visual Studio 特定的設定。 若有選取時，會從 [Gravatar 映射服務](https://en.gravatar.com/)下載作者影像（如果有的話），並顯示在 [認可] 和 [歷程記錄] 視圖中。

:::image type="content" source="media/download-image-setting.png" alt-text="顯示覆選框的螢幕擷取畫面，可讓您從 [選項] 對話方塊中的協力廠商來源下載作者影像。 ":::

>[!IMPORTANT]
>為了在認可和歷程記錄視圖中提供作者映射，此工具會為儲存在作用中存放庫中的作者電子郵件地址建立 MD5 雜湊。 然後，此雜湊會傳送至 Gravatar，以針對先前已註冊服務的使用者尋找相符的雜湊值。 如果找到相符的結果，則會從服務中取出使用者映射，並在 Visual Studio 中顯示。 尚未設定服務的使用者會傳回隨機產生的影像。 請注意，Visual Studio 不會記錄電子郵件地址，也不會與 Gravatar 或任何其他協力廠商共用。

### <a name="commit-changes-after-merge-by-default"></a>依預設在合併後認可變更

當啟用 [ **預設合併後的認可變更] 之後** ，當分支與最新分支合併時，Git 會自動建立新的認可。

:::image type="content" source="media/merge-commit-setting.png" alt-text="螢幕擷取畫面，顯示在 [選項] 對話方塊中預設合併後認可變更的核取方塊。":::

- 若有選取時， `git merge` 會使用選項來執行 Visual Studio 所發出的命令 `--commit` 。
- 若未選取，則 `git merge` 會使用選項來執行 Visual Studio 所發出的命令 `--no-commit --no-ff` 。

如需這些選項的詳細資訊，請參閱 [--commit 和--no 認可](https://git-scm.com/docs/git-merge#Documentation/git-merge.txt---commit) 和 [--no-ff](https://git-scm.com/docs/git-merge#Documentation/git-merge.txt---no-ff)。

### <a name="enable-push---force-with-lease"></a>啟用推播--強制-租用

啟用時，此設定可讓您 `push --force-with-lease` 從 Visual Studio 內進行。 依預設，會停用 **push--force with-租用** 。

:::image type="content" source="media/push-force-setting.png" alt-text="顯示在 [選項] 對話方塊中啟用 [推送強制使用租用] 核取方塊的螢幕擷取畫面。":::

如需詳細資訊，請參閱 [push--強制-租用](https://git-scm.com/docs/git-push#Documentation/git-push.txt---no-force-with-lease)。

### <a name="open-folder-in-solution-explorer-when-opening-a-git-repository"></a>開啟 Git 存放庫時，在方案總管中開啟資料夾
<!-- todo: write section -->
當您使用 Visual Studio 開啟或切換至 Git 存放庫時，Visual Studio 會載入 Git 內容，讓您可以從 IDE 內查看變更、認可、分支，以及管理您的存放庫。 此外，Visual Studio 也會在方案總管中載入存放庫的程式碼。 Visual Studio 將掃描存放庫資料夾中是否有解決方案、CMakeLists.txt 或任何其他可辨識的視圖檔案，並以清單形式顯示在方案總管中。 從該處，您可以選取要載入的解決方案或資料夾來查看目錄內容。 當您關閉此核取方塊時，Visual Studio 將不會在方案總管中開啟存放庫資料夾。 這基本上可讓您以 Git 存放庫管理員的形式開啟 Visual Studio。 此設定預設為開啟。

:::image type="content" source="media/open-folder-setting.png" alt-text="顯示在 [選項] 對話方塊中開啟 Git 儲存機制時，開啟資料夾核取方塊的螢幕擷取畫面。":::

### <a name="automatically-load-the-solution-when-opening-a-git-repository"></a>開啟 Git 存放庫時自動載入解決方案

這項設定僅適用于開啟 [Git 存放庫設定時，方案總管中開啟的資料夾](#open-folder-in-solution-explorer-when-opening-a-git-repository) 。 當您在 Visual Studio 中開啟 Git 存放庫，且後續的資料夾掃描偵測到存放庫中只有一個解決方案時，Visual Studio 會自動載入該解決方案。 如果您關閉此設定，方案總管將會在視圖清單中顯示存放庫中出現的單一解決方案。 但它不會載入方案。 依預設，此設定為 [關閉]。

:::image type="content" source="media/load-solution-setting.png" alt-text="螢幕擷取畫面，顯示在 [選項] 對話方塊中開啟 Git 存放庫時，自動載入解決方案的核取方塊。":::

### <a name="automatically-check-out-branches-with-double-click-or-the-enter-key"></a>按兩下或按 Enter 鍵來自動簽出分支

[Git 存放庫] 視窗有一個顯示在樹狀結構中的分支清單。 單一選取分支將會切換 [認可記錄] 窗格，以顯示所選分支的認可。 若要簽出分支，您可以按一下滑鼠右鍵開啟內容功能表，然後選取 [ **簽出**]。 如果您開啟此設定，按兩下或按下 Enter 鍵將會簽出分支並顯示其認可。 
  
:::image type="content" source="media/checkout-branch-setting.png" alt-text="螢幕擷取畫面，顯示在 [選項] 對話方塊中按兩下或輸入索引鍵來簽出分支的核取方塊。":::


## <a name="see-also"></a>另請參閱

> [!IMPORTANT]
> 如果您對我們有任何建議，請讓我們知道！ 我們很感謝您透過 [**開發人員社群**](https://aka.ms/vsgitsuggestions) 入口網站，在設計決策方面與您互動的機會。

- 在 Microsoft Learn 的 Visual Studio 教學課程[中使用 Git 和 GitHub 開始](/learn/modules/visual-studio-github-push/)
- 在 YouTube 上[Visual Studio 影片中開始使用 Git](https://www.youtube.com/watch?v=GCZ9x3yqkyc)
- [Visual Studio blog 文章中的 Git 增強生產力](https://devblogs.microsoft.com/visualstudio/enhanced-productivity-with-git-in-visual-studio/)
- [選項對話方塊](../ide/reference/options-dialog-box-visual-studio.md)
