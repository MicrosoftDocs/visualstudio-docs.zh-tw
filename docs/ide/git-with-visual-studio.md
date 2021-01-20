---
title: Visual Studio 的 Git 體驗
titleSuffix: ''
description: 瞭解 Visual Studio 2019 中新的整合式 Git 體驗如何協助您提高生產力。
ms.date: 01/15/2021
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
monikerRange: vs-2019
ms.openlocfilehash: 5f93d8c29bcf7e85df04dd364868e65f70482b72
ms.sourcegitcommit: 59b63039982bb5894eb35d8b544657688731614f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98597406"
---
# <a name="git-experience-in-visual-studio"></a>Visual Studio 中的 Git 體驗

Git 現在是 Visual Studio 2019 中的預設版本控制體驗。 自 [16.6 版](/visualstudio/releases/2019/release-notes-v16.6)起，我們已根據您的意見反應來建立功能集並逐一查看。 針對 [版本為 16.8](/visualstudio/releases/2019/release-notes/)的每個人，預設會開啟新的 Git 體驗。

> [!TIP]
> Git 是最廣泛使用的新式版本控制系統，因此無論您是專業開發人員，或是學習如何撰寫程式碼，Git 對您都很有用。 如果您不熟悉 Git， https://git-scm.com/ 網站是不錯的開端。 您可以在這裡找到關於工作表、熱門的線上書籍，以及 Git 基本影片。

## <a name="how-to-use-git-in-visual-studio"></a>如何在 Visual Studio 中使用 Git

我們將逐步引導您瞭解如何在 Visual Studio 2019 中使用新的 Git 體驗，但如果您想要先進行快速導覽，請參閱下列影片： <br><br>*影片長度：5.27 分鐘*

> [!VIDEO https://www.youtube.com/embed/UHrAg3iKoe0]

有三種方式可以開始搭配使用 Git 與 Visual Studio，以提高生產力：

- [開啟現有的 Git 存放庫](#open-an-existing-local-repository)。 如果您的程式碼已經在您的電腦上，您 **可以使用 [** 檔案  >  **開啟**  >  **專案/方案** (] 或 [**資料夾**]) 來開啟該程式碼，Visual Studio 自動偵測是否有已初始化的 Git 存放庫。
- [建立新的 Git 存放庫](#create-a-new-git-repository)。 如果您的程式碼未與 Git 建立關聯，您可以建立新的 Git 存放庫。
- [複製現有的 Git 存放庫](#clone-an-existing-git-repository)。 如果您想要處理的程式碼不在您的電腦上，您可以複製任何現有的遠端存放庫。

> [!NOTE]
> 此外，從 [16.8 版](/visualstudio/releases/2019/release-notes/)開始，Visual Studio 2019 包含完全整合的 GitHub 帳戶體驗。 您現在可以將 GitHub 和 GitHub Enterprise 帳戶新增至 keychain。 您可以像使用 Microsoft 帳戶一樣，加入及使用它們，這表示您可以更輕鬆地跨 Visual Studio 存取 GitHub 資源。 如需詳細資訊，請參閱 [Visual Studio 頁面中的使用 GitHub 帳戶](work-with-github-accounts.md) 。

## <a name="create-a-new-git-repository"></a>建立新的 Git 存放庫

如果您的程式碼未與 Git 相關聯，您可以從建立新的 Git 存放庫開始。 若要這樣做， 請  >  從功能表列選取 [git **建立 git 存放庫**]。 然後，在 [ **建立 Git 存放庫** ] 對話方塊中，輸入您的資訊。

:::image type="content" source="media/git-create-repository.png" alt-text="Visual Studio 中的 [建立 Git 存放庫] 對話方塊。":::

[ **建立 Git 存放庫** ] 對話方塊可讓您輕鬆地將新的存放庫推送至 GitHub。 根據預設，您的新存放庫是私用的，這表示您是唯一可以存取的存放庫。 如果您取消核取此方塊，您的存放庫將會是公用的，這表示 GitHub 上的任何人都可以加以查看。

> [!TIP]
> 無論您的儲存機制是公用或私用，最好是在 GitHub 上安全地儲存程式碼的遠端備份，即使您不是使用小組也是一樣。 無論您使用哪一台電腦，這也可讓您的程式碼可供您使用。

您可以選擇使用 **僅限本機** 選項來建立僅限本機的 Git 存放庫。 或者，您可以使用 **現有的遠端** 選項，將存放庫連結至任何其他 Git 提供者上任何現有的空白遠端存放庫。

## <a name="clone-an-existing-git-repository"></a>複製現有的 Git 存放庫

Visual Studio 包含簡單的複製體驗。 如果您知道想要複製之存放庫的 URL，您可以在 [ **存放庫位置** ] 區段中貼上 url，然後選擇您想要 Visual Studio 複製的磁片位置。

:::image type="content" source="media/git-clone-repository.png" alt-text="在 Visual Studio 中複製 Git 存放庫] 對話方塊。":::

如果您不知道存放庫 URL，Visual Studio 可讓您輕鬆地流覽至現有的 GitHub 或 Azure DevOps 存放庫並加以複製。

### <a name="open-an-existing-local-repository"></a>開啟現有的本機存放庫

複製存放庫或建立存放庫之後，Visual Studio 會偵測到 Git 存放庫，並將其新增至 Git 功能表中的 **本機儲存** 機制清單。 您可以從這裡快速存取並切換 Git 存放庫。

:::image type="content" source="media/git-local-repositories.png" alt-text="Visual Studio 的 Git 功能表中的本機存放庫選項 ":::

## <a name="view-files-in-solution-explorer"></a>在方案總管中查看檔案

當您複製存放庫或開啟本機儲存機制時，Visual Studio 藉由儲存和關閉任何先前開啟的解決方案和專案，將您切換到該 Git 內容。 方案總管會在 Git 存放庫的根目錄載入資料夾，並掃描目錄樹狀結構中的任何視圖檔案。 這些檔案包括 CMakeLists.txt 或副檔名為 .sln 的檔案。

Visual Studio 會根據您在方案總管中載入的視圖檔案來調整其觀點：

- 如果您複製包含單一 .sln 檔案的存放庫，方案總管會為您直接載入該方案。
- 如果方案總管未偵測到存放庫中的任何 .sln 檔案，則預設會載入資料夾檢視。
- 如果您的存放庫有一個以上的 .sln 檔案，則方案總管會顯示可供您選擇的可用視圖清單。

您可以使用 [方案總管] 工具列中的 [ **切換視圖** ] 按鈕，在目前開啟的視圖和視圖清單之間切換。

:::image type="content" source="media/git-solution-explorer-views.png" alt-text="方案總管，並在 Visual Studio 中選取 [切換視圖] 按鈕。":::

## <a name="git-changes-window"></a>Git 變更視窗

當您工作時，Git 會追蹤存放庫中的檔案變更，並將存放庫中的檔案分成三個類別。 這些變更相當於您 `git status` 在命令列中輸入命令時所看到的內容：

- 未 **修改** 的檔案：這些檔案在您上次認可之後未曾變更。
- **修改過** 的檔案：這些檔案在您上次認可之後已變更，但是您尚未暫存這些檔案以進行下一個認可。
- **暫存** 的檔案：這些檔案具有將會新增至下一個認可的變更。

當您執行工作時，Visual Studio 會在 [ **Git 變更**] 視窗的 [**變更**] 區段中，持續追蹤專案的檔案變更。

:::image type="content" source="media/git-changes-window.png" alt-text="Visual Studio 中的 [Git 變更] 視窗。":::

當您準備好要暫存變更時，請按一下 **+** 您要預備的每個檔案上的 (加號) 按鈕，或是以滑鼠右鍵按一下檔案，然後選取 [ **階段**]。 您也可以按一下 [變更] 區段頂端的 [全部] **+** (加) 按鈕，來暫存所有修改過的檔案 。

當您暫存變更時，Visual Studio 會建立 **分段的變更** 區段。 只有 [ **暫存變更** ] 區段中的變更會新增至下一個認可，您可以選取 [ **認可暫存**] 來完成此動作。 此動作的對等命令為 `git commit -m "Your commit message"` 。 您也可以按一下 **–** (減號) 按鈕，來取消暫存變更。 此動作的對等命令是 `git reset <file_path>` 取消暫存單一檔案或 `git reset <directory_path>` 取消臨時目錄中的所有檔案。

您也可以跳過臨時區域，選擇不要暫存修改過的檔案。 在此情況下，Visual Studio 可讓您直接認可變更，而不需要進行暫存。 只需輸入認可訊息，然後選取 [ **全部認可**]。 此動作的對等命令為 `git commit -a` 。

Visual Studio 也可讓您使用 [ **全部認可] 和 [推** 播] 和 [ **全部認可** ] 和 [同步] 快速鍵，輕鬆地進行認可和同步處理。 當您在 [ **變更** ] 和 [ **暫存的變更** ] 區段中按兩下任何檔案時，可以看到與未修改的檔案版本逐行比較。

:::image type="content" source="media/git-file-version-compare.png" alt-text="Visual Studio 中檔案版本的逐行比較 ":::

> [!TIP]
> 如果您連接到 Azure DevOps 存放庫，您可以使用 "#" 字元，將 Azure DevOps 工作專案與認可產生關聯。 您可以透過 **Team Explorer**  >  **管理連接** 來連接 Azure DevOps 存放庫。

### <a name="select-an-existing-branch"></a>選取現有的分支

Visual Studio 會在 [ **Git 變更** ] 視窗頂端的選取器中顯示最新分支。

:::image type="content" source="media/git-changes-current-branch-selector.png" alt-text="目前的分支，您可以在 Visual Studio 中使用 Git 變更選取器頂端的選取器來查看 ":::

Visual Studio IDE 右下角的狀態列也有提供最新分支。

:::image type="content" source="media/git-changes-current-branch-status-bar.png" alt-text="您可以使用 Visual Studio IDE 右下角的狀態列來查看的最新分支 ":::

您可以從這兩個位置切換現有的分支。

### <a name="create-a-new-branch"></a>建立新的分支

您也可以建立新的分支。 此動作的對等命令為 `git checkout <branchname>` 。

建立新的分支就像輸入分支名稱一樣簡單，並將其作為現有分支的基礎。

:::image type="content" source="media/git-changes-create-new-branch.png" alt-text="Visual Studio 中的 [建立新分支] 對話方塊 ":::

您可以選擇現有的本機或遠端分支作為基底。 [ **簽出分支** ] 核取方塊會自動將您切換至新建立的分支。 此動作的對等命令為 `git checkout -b <new-branch><existing-branch>` 。

## <a name="git-repository-window"></a>Git 存放庫視窗

Visual Studio 具有新的 **Git 存放庫** 視窗，此視窗是您存放庫中所有詳細資料的匯總視圖，包括所有分支、遠端和認可記錄。 您可以直接從 **Git** 或在功能表 **欄上或** 從狀態列存取此視窗。

### <a name="manage-branches"></a>管理分支

當您從 **git** 功能表中選取 [**管理分支**] 時，會在 [ **git 存放庫**] 視窗中看到 [分支] 樹狀檢視。 在左窗格中，您可以使用滑鼠右鍵內容功能表來簽出分支、建立新的分支、合併、重定基底、揀選挑選等等。 當您按一下分支時，您可以在右窗格中看到其認可歷程記錄的預覽。

### <a name="incoming-and-outgoing-commits"></a>傳入和傳出認可

當您提取分支時，[ **Git 變更** ] 視窗的 [分支] 下拉式清單底下會有一個指標，會顯示遠端分支的 unpulled 認可數目。 此指標也會顯示未推送本機認可的數目。

:::image type="content" source="media/git-repo-drop-down-indicator.png" alt-text="在 Visual Studio 中顯示指標下拉式 UI 元素的 [Git 變更] 視窗 ":::

指標也可作為連結，將您帶到 **Git 存放庫** 視窗中該分支的認可歷程記錄。 歷程記錄的頂端現在會顯示這些傳入和傳出認可的詳細資料。 從這裡，您也可以決定要提取或推送認可。

:::image type="content" source="media/git-branch-commit-history.png" alt-text="Git 存放庫視窗，顯示 Visual Studio 中分支的認可歷程記錄 ":::

#### <a name="commit-details"></a>認可詳細資料

當您按兩下 **認可** 時，Visual Studio 會在個別的工具視窗中開啟其詳細資料。 您可以從這裡還原認可、重設認可、修改認可訊息，或在認可上建立標記。 當您在認可中按一下變更的檔案時，Visual Studio 會開啟認可及其父系的並列 **差異** 視圖。

:::image type="content" source="media/git-branch-commit-details.png" alt-text="Visual Studio 中的 [認可詳細資料] 對話方塊 ":::

## <a name="handle-merge-conflicts"></a>處理合併衝突

如果有兩個開發人員修改檔案中的相同行，且 Git 不會自動知道哪一個是正確的，則在合併期間可能會發生衝突。 Git 會中止合併，並通知您處於衝突狀態。

Visual Studio 可讓您輕鬆地識別和解決合併衝突。 首先， **Git 存放庫** 視窗會在視窗頂端顯示金色的資訊列。

:::image type="content" source="media/git-merge-conflict-gold-bar.png" alt-text="Visual Studio 中的「合併已完成但發生衝突」訊息 ":::

[ **Git 變更** ] 視窗也會顯示「*合併正在進行中，有衝突*」訊息，並在其下方的個別區段中，將未合併的檔案顯示。

:::image type="content" source="media/git-merge-progress-conflicts-message.png" alt-text="Visual Studio 中的「合併進行中與衝突」訊息 ":::

但是，如果您沒有開啟這兩個視窗，而改為移至有合併衝突的檔案，您就不需要搜尋下列文字：

```bash
    <<<<<<< HEAD
    =======
    >>>>>>> main
```

相反地，Visual Studio 會在頁面頂端顯示金色資訊列，指出開啟的檔案發生衝突。 然後，您可以按一下連結來開啟 [ **合併編輯器**]。

:::image type="content" source="media/git-merge-conflict-gold-info-bar.png" alt-text="Visual Studio 中 [檔案包含合併衝突] 訊息的螢幕擷取畫面 ":::

### <a name="the-merge-editor"></a>合併編輯器

Visual Studio 中的「合併編輯器」是三向合併工具，可顯示內送變更、您目前的變更，以及合併的結果。 您可以使用 **合併編輯器** 最上層的工具列，在衝突與檔案中的自動合併差異之間流覽。

:::image type="content" source="media/git-merge-editor.png" alt-text="Visual Studio 中的合併編輯器 ":::

您也可以使用切換來顯示/隱藏差異、顯示/隱藏字組差異和自訂版面配置。 每一端都有一些核取方塊，可讓您用來從一端或其他部分進行所有變更。 但是若要進行個別變更，您可以按一下任一側的衝突行左邊的核取方塊。 最後，當您完成解決衝突時，可以選取合併編輯器中的 [ **接受合併** ] 按鈕。 然後，您會撰寫認可訊息並認可變更，以完成解決問題。

## <a name="personalize-your-git-settings"></a>將您的 Git 設定個人化

若要在存放庫層級以及全域層級進行個人化和自訂 git 設定，請移至  >  功能表列上的 [git **設定**]，或移至功能表列上的 [**工具**  >  **選項**  >  **原始檔控制**]。 然後，選擇您想要的選項。

:::image type="content" source="media/git-options-settings.png" alt-text="您可以在 Visual Studio IDE 中選擇個人化和自訂設定的 [選項] 對話方塊 ":::

## <a name="how-to-use-the-full-team-explorer-experience-in-visual-studio"></a>如何使用 Visual Studio 的完整 Team Explorer 體驗

新的 Git 體驗是從 [16.8 版](/visualstudio/releases/2019/release-notes/) 開始 Visual Studio 2019 的預設版本控制系統。 但是，如果您想要關閉它，可以。 移至 [**工具**  >  **選項**  >  **環境**  >  **預覽功能**]，然後切換 [**新的 git 使用者體驗**] 核取方塊，這會將您切換回 git 的 Team Explorer。

:::image type="content" source="media/git-opt-new-user-experience.png" alt-text="Visual Studio 中 [選項] 對話方塊的 [預覽功能] 區段 ":::

## <a name="whats-next"></a>後續步驟

雖然新的 Git 體驗現已在 Visual Studio 2019 [16.8 版](/visualstudio/releases/2019/release-notes/)中預設為開啟，但我們仍會繼續新增功能以增強體驗。 如果您想要在預覽版本中查看 Git 體驗的新更新，您可以從 [Visual Studio 預覽](https://aka.ms/vspreview/) 頁面下載並安裝。

> [!IMPORTANT]
> 如果您對我們有任何建議，請讓我們知道！ 我們很感謝您透過 [**開發人員社群**](https://aka.ms/vs-suggest) 入口網站，在設計決策方面與您互動的機會。

## <a name="see-also"></a>另請參閱

- [宣佈推出 Visual Studio blog 文章中的 Git 體驗版本](https://devblogs.microsoft.com/visualstudio/announcing-the-release-of-the-git-experience-in-visual-studio/)
- 在 YouTube 上[推出新的 Git 體驗](https://www.youtube.com/watch?v=UHrAg3iKoe0&t)
- [Visual Studio 工具箱系列提供：](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/The-New-Git-Experience) Channel 9 和[YouTube](https://www.youtube.com/watch?v=ZiQ2LXtAJ6I&feature=youtu.be)上的新 Git 體驗影片
- [Visual Studio blog 文章中的 Git 體驗有很棒的新更新](https://devblogs.microsoft.com/visualstudio/exciting-new-updates-to-the-git-experience-in-visual-studio/)
- [改良 Visual Studio 2019 blog 文章中的 Git 體驗](https://devblogs.microsoft.com/visualstudio/improved-git-experience-in-visual-studio-2019/)
- [在 Visual Studio 中使用 GitHub 帳戶](work-with-github-accounts.md)
- [Visual Studio 2019 版本資訊](/visualstudio/releases/2019/release-notes)
