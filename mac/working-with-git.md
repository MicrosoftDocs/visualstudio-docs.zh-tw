---
title: 使用 Git
description: 在 Visual Studio for Mac 中使用 Git。
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 852B6A9D-AEFA-4EF4-A5DD-94A506019D20
ms.custom: video
ms.openlocfilehash: dc865ec593f53149d9c004f252015def32325d18
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97616173"
---
# <a name="working-with-git"></a>使用 Git

Git 是一種分散式版本控制系統，可讓小組同時處理相同的文件。 這表示有中央伺服器包含所有檔案，但從這個中央來源簽出存放庫時，會將整個存放庫複製至本機電腦。

下列各節將探討如何在 Visual Studio for Mac 中使用 Git 進行版本控制。

## <a name="git-version-control-menu"></a>Git 版本控制功能表

下圖說明 Visual Studio for Mac 透過 [版本控制] 功能表項目所提供的選項：

![版本控制功能表項目](media/version-control-gitVersionControlMenu.png)

## <a name="push-and-pull"></a>推送和提取

推送和提取是 Git 內的兩個最常用動作。 若要同步處理其他人已對遠端存放庫進行的變更，您必須從該處 **提取**。 這是在 Visual Studio for Mac 中完成，方法是選取 [版本控制] > [更新方案]。

在您更新、檢閱並認可檔案之後，接著必須將它們 **推送** 到遠端存放庫，讓其他人可以存取您的變更。 這是在 Visual Studio for Mac 中完成，方法是選取 [版本控制] > [推送變更]。 這會顯示 [推送] 對話方塊以讓您檢視已認可的變更，並選取要推送到其中的分支：

![顯示要認可到其中之分支的對話方塊](media/version-control-gitPush.png)

您也可以透過 [認可] 對話方塊，同時認可並推送您的變更：

![顯示如何同時認可和推送的選項。](media/version-control-commitPush.png)

## <a name="blame-log-and-merge"></a>改動者、記錄和合併

在視窗底部，會顯示五個索引標籤，如下所示：

![版本控制索引標籤](media/version-control-gitTabs.png)

這些允許下列動作：

* **來源** - 顯示原始程式碼檔。
* **變更** - 顯示您的本機檔案與基底檔案之間的程式碼變更。 您也可以比較不同雜湊中檔案的不同版本：

    ![變更索引標籤](media/version-control-gitChange.png)

* **改動者** - 顯示與每個程式碼區段建立關聯之使用者的使用者名稱。
* **記錄** - 顯示所有認可、時間、日期、訊息，以及負責檔案的使用者：

    ![記錄索引標籤](media/version-control-gitLog.png)

* **合併** - 如果您在認可工作時發生合併衝突，則可以使用此項目。 它會以視覺方式呈現您和其他開發人員所做的變更，讓您可以完全合併這兩個程式碼區段。

## <a name="switching-branches"></a>切換分支

根據預設，在存放庫中建立的第一個分支稱為「 **主要** 」分支。 主要分支與任何其他分支之間沒有任何不同的技術，但主要分支是在開發小組中最常被視為「即時」或「生產」分支的分支。

您可以將主要 (或任何其他分支分支，以建立獨立的開發行，就) 。 這可在某個時間點提供新版本的主要分支，讓開發工作獨立于「即時」。 以這種方式使用分支，通常用於軟體開發中的功能

使用者可以針對每個存放庫建立所需數目的分支，但建議在完成分支的使用之後，將它刪除，以保持存放庫的組織性。

瀏覽至 [版本控制] > [管理分支和遠端]，以在 Visual Studio for Mac 中檢視分支：

![分支檢視](media/version-control-gitBranch2.png)

切換至另一個分支，方法是在清單中選取它，並按 [切換至分支] 按鈕。

若要建立新的分支，請選取 [Git 存放庫組態] 對話方塊中的 [新增] 按鈕。 輸入新的分支名稱：

![建立新分支](media/version-control-gitBranch.png)

您也可以將遠端分支設定為 tracking 分支。 請深入閱讀 [Git 文件](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#Tracking-Branches)，以了解如何追蹤分支。

在 [方案] 視窗中，查看專案名稱旁邊的最新分支：

 ![方案視窗中顯示的最新分支](media/version-control-gitBranchName.png)

## <a name="reviewing-and-committing"></a>檢閱並認可

若要檢閱檔案中的變更，請使用每個文件上的 [變更]、[改動者]、[記錄] 和 [合併] 索引標籤，如本主題稍早所示。

瀏覽至 [版本控制] > [Review Solution and Commit] (檢閱方案並認可) 功能表項目，以檢閱專案中的所有變更：

![檢閱程式碼檢視](media/version-control-gitReviewCommit.png)

這允許使用 [還原]、[建立修補檔案] 或 [認可] 的選項來檢視專案之每個檔案中的所有變更。

若要將檔案認可到遠端存放庫，請按 [ **認可**]，輸入認可訊息，然後使用 [認可] 按鈕確認：

![認可檔案](media/version-control-gitCommit.png)

在您認可變更之後，請將它們推送到遠端存放庫，讓其他使用者可以看到它們。

## <a name="related-video"></a>相關影片

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Manage-Projects-with-Git/player]

## <a name="see-also"></a>另請參閱

* [使用 Visual Studio 2017 和 Azure Repos Git 共用您的程式碼](/azure/devops/repos/git/share-your-code-in-git-vs-2017)
