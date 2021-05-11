---
title: Git 和 Team Explorer 在 Visual Studio 中的並列比較
titleSuffix: ''
description: 比較和對比如何使用新的 Git 體驗與 Visual Studio 中的 Team Explorer 來管理原始檔控制。
ms.date: 04/01/2021
ms.topic: how-to
ms.author: tglee
author: TerryGLee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 7f2f8b8bca781e53ab49d34e32a2c0d5ea846ae1
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729333"
---
# <a name="side-by-side-comparison-of-git-and-team-explorer"></a>Git 和 Team Explorer 的並列比較

我們已在 Visual Studio 2019 [16.8 版](/visualstudio/releases/2019/release-notes/)中推出新 Git 體驗的第一個版本。 這種新體驗可透過包含一般 Git 工作的簡單 **Git 變更** 視窗，協助減少內容切換。 它也包含一個全螢幕的 **git 存放庫** 視窗，可進行更先進的 git 作業，例如分支管理和儲存機制流覽。

如果您已經使用 Team Explorer，以下是逐步指南，說明如何使用新的 Git 體驗。

> [!NOTE]
> 下一節包含大小調整以符合資料表資料行大小的螢幕擷取畫面。 按一下每個螢幕擷取畫面，以查看較大的版本。  (如果您使用的是觸控式螢幕裝置，請按一下每個螢幕擷取畫面以查看較大的版本。 ) 

## <a name="get-started"></a>開始使用

|         |Team Explorer  |新的 Git 體驗 |
|---------|---------|---------|
|**複製存放庫** | :::image type="content" source="media/clone-repo-team-explorer-sml.png" alt-text="Visual Studio 2019 中 Team Explorer 的 [連接] 視窗的螢幕擷取畫面，其中包含「複製存放庫」程式重迭。" lightbox="media/clone-repo-team-explorer-lrg.png":::  </p>1. 開啟 [ **連接]** 頁面。 <br> 2. 展開 [ **管理連接**]。 <br> 3. 選取 **[連接到專案]**。 | :::image type="content" source="media/clone-repo-new-git-sml.png" alt-text="Visual Studio 2019 中 Git 功能表的螢幕擷取畫面，其中包含「複製存放庫」程式重迭。" lightbox="media/clone-repo-new-git-lrg.png":::  </p> 1. 開啟 **Git** 功能表。 <br>2. 選取 [ **複製存放庫**]。 <br><br> |
|**在存放庫之間切換**  | :::image type="content" source="media/switch-repos-team-explorer-sml.png" alt-text="Visual Studio 2019 中 Team Explorer 的 [連接] 視窗的螢幕擷取畫面，其中包含 [在存放庫之間切換] 程式重迭。" lightbox="media/switch-repos-team-explorer-lrg.png":::  </p>1. 開啟 [ **連接]** 頁面。 <br>2. 從 **本機存放庫** 清單中選取存放庫。 | :::image type="content" source="media/switch-repos-new-git-sml.png" alt-text="[複製存放庫] 程式重迭的 Visual Studio 2019 中 [本機存放庫] 功能表項目的螢幕擷取畫面。" lightbox="media/switch-repos-new-git-lrg.png"::: </p> 1. 開啟 **Git** 功能表。 <br>2. 從 **本機存放庫** 清單中選取存放庫。  |
|**開啟方案**  |  :::image type="content" source="media/open-solution-team-explorer-sml.png" alt-text="Visual Studio 2019 中 Team Explorer 的主視窗的螢幕擷取畫面，其中包含「開啟方案」程式重迭。" lightbox="media/open-solution-team-explorer-lrg.png":::</p>1. 在 **Team Explorer** 中開啟 **首頁**。 <br>2. 從方案清單中選取方案。  |  :::image type="content" source="media/open-solution-new-git-sml.png" alt-text="Visual Studio 2019 中方案總管的螢幕擷取畫面，其中包含「開啟方案」程式重迭。" lightbox="media/open-solution-new-git-lrg.png":::</p>1. 在 **方案總管** 中開啟 [**切換視圖**] 頁面。 <br>2. 從方案清單中選取方案。  |
|**將方案加入至原始檔控制，並建立新的存放庫**  | :::image type="content" source="media/source-control-team-explorer-sml.png" alt-text="Visual Studio 2019 中 Team Explorer 選項的螢幕擷取畫面，並新增至原始檔控制-建立存放庫程式重迭。" lightbox="media/source-control-team-explorer-lrg.png":::</p>1. 從 [**加入至原始檔控制** 狀態列] 功能表中選取 [ **Git** ]。 <br>2. 選取 [ **發佈**]。  | :::image type="content" source="media/source-control-new-git-sml.png" alt-text="Visual Studio 2019 中 Git 選項的螢幕擷取畫面，其中包含「新增至原始檔控制-建立存放庫」程式重迭。" lightbox="media/source-control-new-git-lrg.png":::</p>1 **. 從 [** **加入至原始檔控制** 狀態列] 功能表中選取 [git]，或從頂層 Visual Studio 功能表列選取 [ **git**  >  **建立 git 存放庫**]。 <br>2. 選取 [ **建立和推送**]。 </p> **注意**：如果您想要將程式碼新增至 Azure DevOps，請使用現有的遠端選項。 在此情況下，您必須先建立 Azure DevOps 存放庫。 |
> [!TIP]
> [新的 Git 體驗](git-with-visual-studio.md)應該會根據您開啟的儲存機制或解決方案，自動連接到正確的 Azure DevOps 存放庫。 但是，如果您需要手動連接到存放庫，您仍然可以使用 Team Explorer 來進行。 從 Visual Studio 的功能表列中，選取 [ **View**  >  **Team Explorer**  >  **管理連接**  >  **連接]**。

## <a name="git-changes"></a>Git 變更

|         |Team Explorer  |新的 Git 體驗 |
|---------|---------|---------|
|**認可和階段** | :::image type="content" source="media/commit-stage-team-explorer-sml.png" alt-text="Visual Studio 2019 中 Team Explorer 的變更視窗的螢幕擷取畫面，其中包含「認可和階段」程式重迭。" lightbox="media/commit-stage-team-explorer-lrg.png":::  </p>1. 輸入認可訊息。 <br>2. 選取 [ **全部認可**]。 <br>3. 若要暫存特定檔案，請以滑鼠右鍵按一下檔案，然後選取 [ **階段**]。  | :::image type="content" source="media/commit-stage-new-git-sml.png" alt-text="Visual Studio 2019 中 [Git 變更] 視窗的螢幕擷取畫面，其中包含「認可和階段」程式重迭。" lightbox="media/commit-stage-new-git-lrg.png"::: </p>1. 輸入認可訊息。 <br>2. 選取 [ **全部認可**]。 <br>3. 若要暫存特定檔案，請將滑鼠停留在其上方，然後按一下 " **+** " 圖示。 |
|**修改認可** |  :::image type="content" source="media/amend-commit-team-explorer-sml.png" alt-text="Visual Studio 2019 中 Team Explorer 的 [變更] 視窗的螢幕擷取畫面，其中含有「修改認可」程式重迭。" lightbox="media/amend-commit-team-explorer-lrg.png":::</p>1. 按一下 [ **動作** ] 下拉式清單。 <br>2. 選取 [ **修改先前的認可**]。 | :::image type="content" source="media/amend-commit-new-git-sml.png" alt-text="Visual Studio 2019 中 [Git 變更] 視窗的螢幕擷取畫面，其中含有「修改認可」程式重迭。" lightbox="media/amend-commit-new-git-lrg.png"::: </p>1. 按一下 [ **修改** ] 核取方塊。 <br>2. 按一下 [ **全部認可** ] 以認可您的更新。  |
|**隱藏變更** | :::image type="content" source="media/stash-change-team-explorer-sml.png" alt-text="Visual Studio 2019 中 Team Explorer 的 [變更] 視窗的螢幕擷取畫面，其中包含「隱藏變更」程式重迭。" lightbox="media/stash-change-team-explorer-lrg.png":::</p>1. 按一下 [ **隱藏** ] 下拉式清單。 <br>2. 選取相關的 **隱藏** 專案選項。 | :::image type="content" source="media/stash-change-new-git-sml.png" alt-text="使用「隱藏變更」程式重迭的 Visual Studio 2019 中 [Git 變更] 視窗的螢幕擷取畫面。" lightbox="media/stash-change-new-git-lrg.png":::</p>1. 按一下 [ **全部認可** ] 下拉式清單。 <br>2. 選取相關的 **隱藏** 專案選項。 |

## <a name="synchronization"></a>同步處理

|         |Team Explorer  |新的 Git 體驗 |
|---------|---------|---------|
|**提取、提取和推送變更** | :::image type="content" source="media/fetch-pull-push-team-explorer-sml.png" alt-text="Visual Studio 2019 中 Team Explorer 的 [同步處理] 視窗的螢幕擷取畫面，其中包含「提取、提取和推送」程式重迭。" lightbox="media/fetch-pull-push-team-explorer-lrg.png":::</p>1. 流覽至 [ **同步** 處理] 頁面。 <br>2. 按一下您選擇的網路作業。 | :::image type="content" source="media/fetch-pull-push-new-git-sml.png" alt-text="Visual Studio 2019 中 [Git 變更] 視窗的螢幕擷取畫面，其中包含「提取、提取和推送」程式重迭。" lightbox="media/fetch-pull-push-team-new-git-lrg.png"::: </p>1. 在 [ **Git 變更** ] 視窗中找出提取、提取和推送按鈕。 <br>2. 按一下您選擇的網路作業。|
|**查看傳入和傳出認可** | :::image type="content" source="media/view-commits-team-explorer-sml.png" alt-text="Visual Studio 2019 中 Team Explorer 的 [同步處理] 視窗的螢幕擷取畫面，其中包含「view 傳入和傳出認可」程式重迭。" lightbox="media/view-commits-team-explorer-lrg.png"::: </p>1. 流覽至 [ **同步** 處理] 頁面。 <br>2. 查看您的連入和連出列表。 | :::image type="content" source="media/view-commits-new-git-sml.png" alt-text="[Git 變更] 視窗的螢幕擷取畫面，以及 Visual Studio 2019 中的 Git 存放庫視窗，其中含有「查看傳入和傳出的認可」程式重迭。" lightbox="media/view-commits-new-git-lrg.png":::</p>1. 在 [ **Git 變更**] 視窗中，按一下 **外寄/連入** 連結。 <br>2. 在 **Git 存放庫** 視窗頂端的圖形資料表中，使用圖示來查看傳入和傳出的認可。 |

## <a name="branches"></a>分支

|         |Team Explorer  |新的 Git 體驗 |
|---------|---------|---------|
|**建立分支** |  :::image type="content" source="media/create-branch-team-explorer-sml.png" alt-text="Visual Studio 2019 中 Team Explorer 的 [分支] 視窗的螢幕擷取畫面，其中包含 [建立新分支] 程式重迭。" lightbox="media/create-branch-team-explorer-lrg.png":::</p>1. 流覽至 [ **分支** ] 視窗。 <br> 2. 按一下 [ **新增分支**]。 | :::image type="content" source="media/create-branch-new-git-sml.png" alt-text="Visual Studio 2019 中 [Git 變更] 視窗的螢幕擷取畫面，其中包含 [建立新分支] 程式重迭。" lightbox="media/create-branch-new-git-lrg.png"::: </p>1. 在 [ **Git 變更** ] 視窗上，按一下 [分支] 下拉式清單。 <br>2. 按一下 [ **新增分支**]。 |
|**從遠端分支取得最新的變更** | :::image type="content" source="media/sync-remote-team-explorer-sml.png" alt-text="Visual Studio 2019 中 Team Explorer 的 [分支] 視窗的螢幕擷取畫面，其中包含「從遠端分支取得最近的變更」程式重迭。" lightbox="media/sync-remote-team-explorer-lrg.png"::: </p>1. 流覽至 [ **分支] 頁面**。 <br>2. 以滑鼠右鍵按一下遠端分支，然後選取 [ **合併來源** ] 或 [重 **基** 底]。  | :::image type="content" source="media/sync-remote-new-git-sml.png" alt-text="Visual Studio 2019 中 [Git 變更] 視窗的螢幕擷取畫面，其中包含「從遠端分支取得最近的變更」程式重迭。" lightbox="media/sync-remote-new-git-lrg.png":::</p>1. 按一下 [分支] 下拉式清單。 <br>2 **. 在 [遠端] 索引** 標籤下，按一下 [遠端] 分支，然後選取 [ **合併到最新分支** 或重訂 **基底最新分支**。  |
|**管理分支** | :::image type="content" source="media/manage-branches-team-explorer-sml.png" alt-text="Visual Studio 2019 中 Team Explorer 的 [分支] 視窗的螢幕擷取畫面，其中包含 [管理分支] 程式重迭。" lightbox="media/manage-branches-team-explorer-lrg.png"::: </p>1. 流覽至 [ **分支** ] 視窗。 <br>2. 以滑鼠右鍵按一下您想要管理的分支。 <br>3. 查看分支的歷程 **記錄** 以管理認可。 | :::image type="content" source="media/manage-branches-new-git-sml.png" alt-text="螢幕擷取畫面：如何使用三個 UI 選項來管理 Visual Studio 2019 中的分支。" lightbox="media/manage-branches-new-git-lrg.png"::: </p>1. 使用下列其中一個進入點流覽至 Git 存放庫視窗： <br><br>a. 從最上層的 Visual Studio 功能表中，選取 [ **Git**  >  **管理分支**]。<br> b. 選取 [ **Git 變更** 連  >  **入/連出**]。 <br>c. 從右下方的狀態列功能表中，選取 [ **管理分支**]。<br> <br> 2. 從最上層的 [ **Git**  >  **管理分支**] 功能表中，執行下列其中一個動作： <br><br>A. 以滑鼠右鍵按一下 [分支]。<br>B. 多重選取您要管理的認可。 |

## <a name="conflict-resolution"></a>衝突解決

|         |Team Explorer  |新的 Git 體驗 |
|---------|---------|---------|
|**存取有衝突的檔案清單** | :::image type="content" source="media/resolve-conflicts-team-explorer-sml.png" alt-text="變更視窗的螢幕擷取畫面，以及 Visual Studio 2019 中 Team Explorer 的 [解決衝突] 視窗，以及程式重迭。" lightbox="media/resolve-conflicts-team-explorer-lrg.png":::</p>1. 按一下 [**衝突**] 連結，以流覽至 [**解決衝突**] 視窗。 <br> 2. 使用 **衝突** 清單來解決合併衝突。 | :::image type="content" source="media/resolve-conflicts-new-git-sml.png" alt-text="Visual Studio 2019 中 [Git 變更] 視窗的螢幕擷取畫面，其中包含 [解決衝突] 程式重迭。" lightbox="media/resolve-conflicts-new-git-lrg.png"::: </p>1. 確認 [ **合併進行中] 發生衝突** 。 <br>2. 包含合併衝突的檔案清單會出現在 [ **Git 變更**] 視窗的 [未 **合併的變更**] 區段中。 <br>解決衝突。 |

## <a name="next-steps"></a>下一步

如需有關新 Git 體驗的詳細資訊，請參閱 YouTube 上的最新影片： [Visual Studio 的 Git 入門](https://www.youtube.com/watch?v=GCZ9x3yqkyc)。

## <a name="see-also"></a>另請參閱

- [Visual Studio 的新 Git 體驗](git-with-visual-studio.md)
- [Visual Studio 中的 Git 和 GitHub 開始](/learn/modules/visual-studio-github-push/)
- [在 Visual Studio 中使用 GitHub 帳戶](../ide/work-with-github-accounts.md)