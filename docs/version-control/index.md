---
layout: LandingPage
title: Visual Studio 中的版本控制 | VSTS 與 TFS
description: Visual Studio 中的版本控制使用者入門指南
keywords: VSTS, TFS, 版本控制
author: steved0x
ms.manager: douge
ms.author: sdanie
ms.date: 12/15/2017
ms.topic: landing-page
ms.prod: .net-core
ms.assetid: 2c119a5f-0272-48c0-8d6c-806196944aea
ms.workload:
- multiple
ms.openlocfilehash: e37645f8960aae54907dffeb0bcb88848d9cd63f
ms.sourcegitcommit: 28909340cd0a0d7cb5e1fd29cbd37e726d832631
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44320575"
---
# <a name="version-control-in-visual-studio"></a>Visual Studio 中的版本控制

版本控制系統可協助您追蹤程式碼隨著時間的變更。 當您進行變更時，版本控制系統就會為您的檔案建立快照。 版本控制系統會永久儲存快照，讓您可以在稍後需要時叫用。 Visual Studio 提供 [Git](/azure/devops/repos/git/index?view=vsts) 與 [Team Foundation 版本控制 (TFVC)](/azure/devops/repos/tfvc/index?view=vsts)。 若要在兩種系統之間下決定，請參閱[為您的專案選擇合適的版本控制](/azure/devops/repos/tfvc/comparison-git-tfvc?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json)。

## <a name="git"></a>Git
Git 是現今最常使用的版本控制系統，並且快速成為版本控制標準。 Git 是分散式版本控制系統，亦即您的本機程式碼複本即是完整的版本控制存放庫。 這些功能完整的本機存放庫讓離線或從遠端工作變得更加容易。 您在本機認可您的工作，然後將存放庫的複本與伺服器上的複本同步。 此種模式與集中式版本控制不同。集中式版本控制的用戶端必須與伺服器同步程式碼，之後才能建立新版本的程式碼。

<ul class="panelContent cardsFTitle">
    <li>
        <a href="https://docs.microsoft.com/azure/devops/git/what-is-git">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>了解 Git</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/git/share-your-code-in-git-vs-2017?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>藉由 Visual Studio 使用 Git 的使用者入門</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/git/clone?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>複製現有的 Git 存放庫</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>

## <a name="tfvc"></a>TFVC

Team Foundation 版本控制 (TFVC) 是集中式版本控制系統。 一般而言，小組成員的開發電腦上每個檔案只有一個版本。 只在伺服器上維護記錄資料。 分支以路徑為基礎，在伺服器上建立。

<ul class="panelContent cardsFTitle">
    <li>
        <a href="/azure/devops/repos/tfvc/overview">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>了解 TFVC</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Visual Studio 中的 TFVC 使用者入門</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
   <li>
        <a href="/azure/devops/repos/tfvc/get-code-reviewed-vs?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>檢閱您的程式碼</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>


## <a name="resources"></a>資源

- [Pro Git 書籍](https://git-scm.com/book/en/v2)
- [規劃移轉至 Git](https://docs.microsoft.com/azure/devops/git/centralized-to-git) \(英文\)
- [從 TFVC 移轉至 Git](https://docs.microsoft.com/azure/devops/git/migrate-from-tfvc-to-git) \(英文\)