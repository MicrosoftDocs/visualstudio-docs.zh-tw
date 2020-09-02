---
title: 在 Team Explorer 中連線到專案
ms.date: 07/07/2020
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
ms.openlocfilehash: bddb3afb602416159c75a5be9923fce14c089fc2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "86181049"
---
# <a name="connect-to-projects-in-team-explorer"></a>在 Team Explorer 中連線到專案

您可以使用 **Team Explorer** 工具視窗協調與其他小組成員合作開發專案時的程式碼撰寫工作，以及管理指派給您、小組或專案的工作。 **Team Explorer** 會將 Visual Studio 連線到 Git 和 GitHub 存放庫、Team Foundation 版本控制 (TFVC) 存放庫，以及裝載於 [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) 或內部部署 [Azure DevOps Server](/azure/devops/index-all) (之前稱為 TFS) 的專案。 您可以管理原始程式碼、工作項目和組建。

![Visual Studio 中的 Team Explorer [首頁]](media/team-explorer/team-explorer.png)

> [!TIP]
> 如果您開啟 Visual Studio 但**Team Explorer**未出現，請從功能表列選擇 [ **View**  >  **Team Explorer** ]，或按**ctrl** + **&#92;**、 **ctrl** + **M**來開啟它。

## <a name="connect-to-a-project-or-repository"></a>連線到專案或存放庫

在 [連線]**** 頁面上，連線到專案或存放庫。

![Team Explorer 中的 [連線] 頁面](media/team-explorer/connect.png)

若要連線到專案：

1. 選擇**管理連線**圖示，以開啟 [連線]**** 頁面。

   ![Team Explorer 中的 [管理連線] 按鈕](media/team-explorer/manage-connections.png)

1. 在 [連線]**** 頁面上，選擇 [管理連線]**** > [連線到專案]****。

   ![在 Team Explorer 中連線到專案](media/team-explorer/connect-project.png)

> [!TIP]
> 如果您想要從存放庫開啟專案，請參閱 [從存放庫開啟專案](../get-started/tutorial-open-project-from-repo.md)。 如果您想要建立新的專案，或將使用者加入至專案，請參閱 [建立專案 (Azure DevOps) ](/azure/devops/organizations/projects/create-project) 並 [將使用者新增至專案或小組 (Azure DevOps) ](/azure/devops/organizations/security/add-users-team-project)。

## <a name="see-also"></a>另請參閱

- [教學課程：從存放庫開啟專案](../get-started/tutorial-open-project-from-repo.md)
- [Team Explorer 參考](reference/team-explorer-reference.md)
- [連線到專案 (Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects)
- [針對連接到專案進行疑難排解](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops)
