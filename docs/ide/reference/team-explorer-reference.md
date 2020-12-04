---
title: Team Explorer 參考
description: 瞭解 Team Explorer 中的各種功能，以管理工作並與其他小組成員協調以開發專案。
ms.custom: SEO-VS-2020
ms.date: 12/04/2018
ms.topic: reference
ms.author: kaelli
author: KathrynEE
ms.manager: jillfra
ms.openlocfilehash: a7089defb41c3ba8379d1020cbf1225d6333b912
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560989"
---
# <a name="team-explorer-reference"></a>Team Explorer 參考

本文提供 **Team Explorer** 中各項功能的相關 Azure DevOps 文章連結。

您可以使用 **Team Explorer** 工具視窗協調與其他小組成員合作開發專案時的程式碼撰寫工作，以及管理指派給您、小組或專案的工作。 **Team Explorer** 會將 Visual Studio 連線到 Git 和 GitHub 存放庫、Team Foundation 版本控制 (TFVC) 存放庫，以及裝載於 [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) 或內部部署 [Azure DevOps Server](/azure/devops/index-all) (之前稱為 TFS) 的專案。 您可以管理原始程式碼、工作項目和組建。

## <a name="home-page"></a>首頁

在 **Team Explorer** 中 [連線到專案](../connect-team-project.md)之後，即可在 [專案] 區段中使用下列連結：

- [複製存放庫](/azure/devops/repos/git/clone)
- [入口網站](/azure/devops/project/navigation/index)
- [工作面板](/azure/devops/boards/sprints/task-board)

根據您是連線到 [Git](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio&preserve-view=true) 或 [Team Foundation 版本控制 (TFVC)](/azure/devops/repos/tfvc/overview) 存放庫，[首頁] 會有不同的功能。

> [!TIP]
> 如需比較這兩種版本控制系統，請參閱[為您的專案選擇正確版本控制 (Azure DevOps)](/azure/devops/repos/tfvc/comparison-git-tfvc)。

| 含 Git 的 [首頁] | 含 TFVC 的 [首頁] |
| - | - |
| ![Visual Studio 2019 中含 Git 的 Team Explorer [首頁]](media/team-explorer-reference/team-explorer-git.png) | ![Visual Studio 中含 TFVC 的 Team Explorer [首頁]](media/team-explorer-reference/team-explorer-tfvc.png) |

## <a name="changes-page-git"></a>變更頁面 (Git)

請參閱[使用認可來儲存工作](/azure/devops/repos/git/commits)。

## <a name="branches-page-git"></a>分支頁面 (Git)

請參閱[在分支中建立工作](/azure/devops/repos/git/branches)。

## <a name="pull-requests-page-git"></a>提取要求頁面 (Git)

請參閱[使用提取要求來檢閱程式碼](/azure/devops/repos/git/pullrequest)。

## <a name="sync-page-git"></a>同步頁面 (Git)

請參閱[使用擷取與提取來更新程式碼](/azure/devops/repos/git/pulling)。

## <a name="tags-page-git"></a>標記頁面 (Git)

請參閱[使用 Git 標記](/azure/devops/repos/git/git-tags)。

## <a name="my-work-page-tfvc"></a>我的工作頁面 (TFVC)

請參閱[暫止/繼續工作](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets)和[程式碼檢閱](/azure/devops/repos/tfvc/day-life-alm-developer-suspend-work-fix-bug-conduct-code-review)。

## <a name="pending-changes-page-tfvc"></a>暫止的變更頁面 (TFVC)

請參閱[管理暫止的變更](/azure/devops/repos/tfvc/develop-code-manage-pending-changes)、[尋找擱置集](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets)和[解決衝突](/azure/devops/repos/tfvc/resolve-team-foundation-version-control-conflicts)。

## <a name="source-control-explorer-page-tfvc"></a>原始檔控制總管頁面 (TFVC)

請參閱[新增/檢視檔案與資料夾](/azure/devops/repos/tfvc/add-files-server)。

## <a name="work-items-page"></a>工作項目頁面

[工作項目] 頁面可讓您查看[工作項目](/azure/devops/boards/work-items/about-work-items)查詢。 請參閱：

- [新增工作項目](/azure/devops/boards/backlogs/add-work-items)
- [使用查詢編輯器列出和管理查詢](/azure/devops/boards/queries/using-queries)
- [組織查詢資料夾和設定查詢權限](/azure/devops/boards/queries/set-query-permissions)
- [在 Excel 中開啟查詢](/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel)
- [在 Project 中開啟查詢](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)
- [使用 Outlook 透過電子郵件傳送查詢結果清單](/azure/devops/boards/queries/share-plans)
- [從 Excel 中的查詢建立報表](/azure/devops/report/excel/create-status-and-trend-excel-reports) (僅限 TFS)

::: moniker range=">= vs-2019"

> [!NOTE]
> Visual Studio 2019 提供新的[工作項目體驗](/azure/devops/boards/work-items/set-work-item-experience-vs)。 如需如何在 Visual Studio 2019 中檢視工作項目的資訊，請參閱[檢視和新增工作項目](/azure/devops/boards/work-items/view-add-work-items)。

::: moniker-end

## <a name="builds-page"></a>組建頁面

[組建] 頁面可讓您查看專案的組建定義。

請參閱：

- [建立組建路線](/azure/devops/pipelines/tasks/index)
- [檢視和管理組建](/azure/devops/pipelines/overview)
- [管理組建佇列](/azure/devops/pipelines/agents/pools-queues)
- [安裝 Visual Studio 持續傳遞 (CD) 工具](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#install-continuous-delivery-cd-tools-for-visual-studio-2017)
- [為您的應用程式設定和執行持續傳遞 (CD)](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#configure-and-execute-continuous-delivery-cd-for-your-app)

## <a name="settings-page"></a>設定頁面

[設定] 頁面可讓您為專案或專案集合設定管理功能。 查看下列文章：

| Project | 專案集合 | 其他 |
| - | - | - |
| [安全性、群組成員資格](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[安全性、原始檔控制 (TFVC)](/azure/devops/organizations/security/set-git-tfvc-repository-permissions)<br/>[工作項目區域](/azure/devops/organizations/settings/set-area-paths)<br/>[工作項目反覆項目](/azure/devops/organizations/settings/set-iteration-paths-sprints)<br/>[入口網站設定](/azure/devops/report/sharepoint-dashboards/configure-or-add-a-project-portal)<br/>[專案警示](/azure/devops/notifications/howto-manage-team-notifications) | [安全性、群組成員資格](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[原始檔控制 (TFVC)](/azure/devops/repos/tfvc/decide-between-using-local-server-workspace)<br/>[流程範本管理員](/azure/devops/boards/work-items/guidance/manage-process-templates) | [Git 全域設定](/azure/devops/repos/git/git-config)<br/>[Git 存放庫設定](/azure/devops/repos/git/git-config) |

## <a name="see-also"></a>另請參閱

- [在 Team Explorer 中連線到專案](../../ide/connect-team-project.md)