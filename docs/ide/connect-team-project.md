---
title: 在 Team Explorer 中連線到專案
description: 瞭解如何使用 Visual Studio 中的 Team Explorer，與小組成員合作來開發和管理專案。
ms.custom: SEO-VS-2020
ms.date: 03/31/2021
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
ms.openlocfilehash: 78a71911bb4334e04a085d91ff51238d34981beb
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216601"
---
# <a name="connect-to-projects-in-team-explorer"></a>在 Team Explorer 中連線到專案

::: moniker range="vs-2017"

您可以使用 **Team Explorer** 工具視窗協調與其他小組成員合作開發專案時的程式碼撰寫工作，以及管理指派給您、小組或專案的工作。 **Team Explorer** 會將 Visual Studio 連線到 Git 和 GitHub 存放庫、Team Foundation 版本控制 (TFVC) 存放庫，以及裝載於 [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) 或內部部署 [Azure DevOps Server](/azure/devops/index-all) (之前稱為 TFS) 的專案。 您可以管理原始程式碼、工作項目和組建。

::: moniker-end

::: moniker range="vs-2019"

Team Explorer 會將 Visual Studio 連接至 Team Foundation 版本控制 (TFVC) 儲存機制，以及裝載于 [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) 或內部部署 [Azure DevOps Server](/azure/devops/user-guide/about-azure-devops-services-tfs?view=azure-devops&preserve-view=true) (上的專案（先前稱為 TFS) ）。 您可以管理原始程式碼、工作項目和組建。

> [!IMPORTANT]
> 在最新版本的 Visual Studio 2019 [**16.8 版**](/visualstudio/releases/2019/release-notes/)中，現在預設會開啟新的 Git 版本控制體驗。 如果您想要深入瞭解它與 Team Explorer 的比較，請參閱 [**Git 和 Team Explorer 頁面的並列比較**](git-team-explorer-feature-comparison.md) 。
>
> 但是，如果您想要繼續使用 Team Explorer，請移至 [ **工具** > **選項** > **環境** > **預覽功能** ]，然後切換 [ **新的 Git 使用者體驗** ] 核取方塊。

您使用 Team Explorer 連接到專案的方式，取決於您所使用的 Visual Studio 2019 版本。

## <a name="in-version-168-and-later"></a>在16.8 版和更新版本中

1. 開啟 Visual Studio 2019。

1. 在 [開始] 視窗中，選取 [ **複製存放庫**]。

   ![在 Visual Studio 2019 16.8 版和更新版本的 [複製存放庫] 對話方塊的螢幕擷取畫面，適用于 Azure DevOps](../ide/media/vs-2019/clone-repository.png)

1. 在 [ **流覽存放庫]** 區段中，選取 [ **Azure DevOps**]。

    ![在 Visual Studio 2019 16.8 版和更新版本中，[連線到專案] 對話方塊的 [流覽儲存機制] 區段的螢幕擷取畫面](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. 如果您看到登入視窗，請登入您的帳戶。

1. 在 [ **連接到專案** ] 對話方塊中，選擇您要連接的存放庫，然後選取 [ **複製**]。

      ![從 Visual Studio 2019 16.8 版和更新版本產生的 [連線到專案] 對話方塊的螢幕擷取畫面](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > 如果您沒有看到要連接的存放庫預先填入清單，請選取 [ **新增 Azure DevOps Server** 以輸入伺服器 URL。  (或者，您可能會看到「找不到伺服器」提示，其中包含新增現有 Azure DevOps Server 或建立 Azure DevOps 帳戶的連結。 ) 

   接著，Visual Studio 會開啟顯示資料夾和檔案的 **方案總管** 。

1. 選取 [ **Team Explorer** ] 索引標籤，以查看 Azure DevOps 動作。

      ![從 Visual Studio 2019 16.8 版和更新版本產生的 [Team Explorer] 對話方塊的螢幕擷取畫面](../ide/media/vs-2019/team-explorer-azure-devops.png)

## <a name="in-version-167-and-earlier"></a>在16.7 版和更舊版本中

1. 開啟 Visual Studio 2019。

1. 在 [開始] 視窗中，選取 [ **複製或簽出程式碼**]。

   ![[建立新專案] 視窗的螢幕擷取畫面，在 Visual Studio 2019 16.7 版及更早版本中](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. 在 [ **流覽存放庫]** 區段中，選取 [ **Azure DevOps**]。

   ![[複製或簽出程式碼] 視窗的螢幕擷取畫面，其中會列出 Visual Studio 2019 16.7 版及更早版本中 Azure DevOps 的 [流覽儲存機制] 區段](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   如果您看到登入視窗，請登入您的帳戶。

1. 在 [ **連接到專案** ] 對話方塊中，選擇您要連接的存放庫，然後選取 [ **複製**]。

      ![[連線到專案] 對話方塊的螢幕擷取畫面，此對話方塊是從 Visual Studio 2019 16.7 版及更早版本所產生](../get-started/media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > 您在清單方塊中看到的內容，取決於您有權存取的 Azure DevOps 存放庫。

   Visual Studio 會開啟 [Team Explorer]，並在複製完成時顯示通知。

     ![複製完成之後，Visual Studio 2019 16.7 版及更早版本中 Team Explorer 視窗的螢幕擷取畫面](../get-started/media/vs-2019/clone-complete-azure-devops.png)

1. 若要查看您的資料夾和檔案，請選取 [ **顯示資料夾視圖** ] 連結。

     ![在複製完成之後，Visual Studio 2019 16.7 版及更早版本中，[Team Explorer] 視窗的 [解決方案] 區段螢幕擷取畫面](../get-started/media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio 會開啟 [方案總管]。

1. 選擇 [ **方案和資料夾** ] 連結，以搜尋解決方案檔 (具體而言，就是開啟) 的 .sln 檔案。

      ![Visual Studio 2019 16.7 版及更早版本中 Team Explorer 的「解決方案和資料夾」通知螢幕擷取畫面](../get-started/media/open-proj-repo-solutions-folders.png)

   如果您的存放庫中沒有解決方案檔，則會出現「找不到任何解決方案」訊息。 不過，您可以從資料夾功能表中按兩下任一檔案，以便在 Visual Studio 程式碼編輯器中開啟該檔案。

::: moniker-end

::: moniker range="vs-2017"

![Visual Studio 中的 Team Explorer [首頁]](media/team-explorer/team-explorer.png "Visual Studio 中的 Team Explorer 首頁。")

> [!TIP]
> 如果您開啟 Visual Studio 但 **Team Explorer** 未出現，請從功能表列選擇 [ **View**  >  **Team Explorer** ]，或按 **ctrl** + **&#92;**、 **ctrl** + **M** 來開啟它。

## <a name="connect-to-a-project-or-repository"></a>連線到專案或存放庫

在 [連線] 頁面上，連線到專案或存放庫。

![Team Explorer 中的 [連線] 頁面](media/team-explorer/connect.png "Visual Studio 中的 [Team Explorer 連接] 頁面")

若要連線到專案：

1. 選擇 **管理連線** 圖示，以開啟 [連線] 頁面。

   ![Team Explorer 中的 [管理連線] 按鈕](media/team-explorer/manage-connections.png "Visual Studio 中的 [Team Explorer-管理連接] 按鈕。")

1. 在 [連線] 頁面上，選擇 [管理連線]**[連線到專案]** > 。

   ![在 Team Explorer 中連線到專案](media/team-explorer/connect-project.png "Team Explorer-連接到 Visual Studio 中的專案選項。")

> [!TIP]
> 如果您想要從存放庫開啟專案，請參閱 [從存放庫開啟專案](../get-started/tutorial-open-project-from-repo-visual-studio-2017.md)。 如果您想要建立新的專案，或將使用者加入至專案，請參閱 [建立專案 (Azure DevOps) ](/azure/devops/organizations/projects/create-project) 並 [將使用者新增至專案或小組 (Azure DevOps) ](/azure/devops/organizations/security/add-users-team-project)。

::: moniker-end

## <a name="see-also"></a>另請參閱

- [比較 Git 和 Team Explorer 並存](git-team-explorer-feature-comparison.md)
- [Visual Studio 的新 Git 體驗](git-with-visual-studio.md)
- [Team Explorer 參考](reference/team-explorer-reference.md)
- [連線到專案 (Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects)
- [針對連接到專案進行疑難排解](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops&preserve-view=true)
