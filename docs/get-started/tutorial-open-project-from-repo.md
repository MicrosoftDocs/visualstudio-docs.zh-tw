---
title: 教學課程：從存放庫開啟專案
description: 了解如何使用 Visual Studio，在 Git 或 Azure DevOps 存放庫中開啟專案。
ms.custom: get-started
ms.date: 03/30/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b1796ca10226e4aa5d0242bea89cc01f8452cf9e
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402077"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>教學課程：從存放庫開啟專案

在本教學課程中，您將第一次使用 Visual Studio 連線到存放庫，然後從中開啟專案。

::: moniker range="vs-2017"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2019"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)頁面免費進行安裝。

::: moniker-end

## <a name="open-a-project-from-a-github-repo"></a>從 GitHub 存放庫開啟專案

::: moniker range="vs-2017"

1. 開啟 Visual Studio 2017。

1. 從頂端的功能表列中，選擇 [檔案]  > [開啟]  > [從原始檔控制開啟]  。

   [Team Explorer - 連接]  窗格隨即開啟。

    ![Visual Studio IDE 中的 [Team Explorer] 視窗](./media/open-proj-repo-team-explorer.png)

1. 在 [本機 Git 存放庫]  區段中，選擇 [複製]  。

    ![從 [本機 Git 存放庫] 區段中選擇 [複製]](./media/open-proj-repo-local-git-repo-clone.png)

1. 在 [輸入要複製的 Git 存放庫的 URL ] 方塊中，輸入或貼上您存放庫的 URL，然後按 **Enter** (您可能會看見登入 GitHub 的提示；如果看見提示，請登入)。

   當 Visual Studio 複製您的存放庫之後，[Team Explorer] 即會關閉，而 [方案總管] 即會開啟。 隨即出現一則訊息，指出「按一下上方的 [解決方案與資料夾] 可檢視解決方案清單」  。 選擇 [解決方案與資料夾]  。

   ![從 [方案總管] 中選擇 [解決方案與資料夾]](./media/open-proj-repo-github-solutions-folders.png)

1. 如果您有可用的解決方案檔，它將會出現在 [解決方案與資料夾] 飛出功能表中。 選擇它，而 Visual Studio 會開啟您的解決方案。

   ![選擇您想要從 [方案總管] 下拉式清單中開啟的解決方案](./media/open-proj-repo-github-solutions-folders-picker.png)

   如果您的存放庫中沒有解決方案檔 (具體來說為 .sln 檔案)，飛出功能表將顯示「找不到任何解決方案」。 不過，您可以從資料夾功能表中按兩下任一檔案，以便在 Visual Studio 程式碼編輯器中開啟該檔案。

### <a name="review-your-work"></a>檢閱您的工作

檢視以下動畫以檢查您在上一節中完成的工作。

   ![使用 Visual Studio 在 GitHub 存放庫中開啟專案的動畫](./media/open-project-from-github.gif)

::: moniker-end

::: moniker range="vs-2019"

1. 開啟 Visual Studio 2019。

1. 在開始視窗中，選擇 [複製或簽出程式碼]  。

   ![檢視 [建立新專案] 視窗](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. 輸入或鍵入存放庫的位置，然後選擇 [複製]  。

   ![檢視 [複製或簽出程式碼] 視窗](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio 從存放庫開啟專案。

1. 如果您有可用的解決方案檔，它將會出現在 [解決方案與資料夾] 飛出功能表中。 選擇它，而 Visual Studio 會開啟您的解決方案。

   ![選擇您想要從 [方案總管] 下拉式清單中開啟的解決方案](./media/open-proj-repo-github-solutions-folders-picker.png)

   如果您的存放庫中沒有解決方案檔 (具體來說為 .sln 檔案)，飛出功能表將顯示「找不到任何解決方案」。 不過，您可以從資料夾功能表中按兩下任一檔案，以便在 Visual Studio 程式碼編輯器中開啟該檔案。

::: moniker-end

## <a name="open-a-project-from-an-azure-devops-repo"></a>從 Azure DevOps 存放庫中開啟專案

::: moniker range="vs-2017"

1. 開啟 Visual Studio 2017。

1. 從頂端的功能表列中，選擇 [檔案]  > [開啟]  > [從原始檔控制開啟]  。

   [Team Explorer - 連接]  窗格隨即開啟。

    ![Visual Studio IDE 中的 [Team Explorer] 視窗](./media/open-proj-repo-team-explorer.png)

1. 以下是兩種可連線到您 Azure DevOps 存放庫的方式：

      - 在 [託管服務提供者]  區段中，選擇 [連線...]  .

        ![Visual Studio IDE 內 [Team Explorer] 視窗的 [託管服務提供者] 區段](./media/open-proj-repo-azure-devops.png)

      - 在 [管理連線]  下拉式清單中，選擇 [連線到專案...]  。

        ![Visual Studio IDE 內 [Team Explorer] 視窗的 [管理連線] 區段](./media/open-proj-repo-azuredevops-manage-connections.png)

1. 在 [連線到專案]  對話方塊中，選擇您想要連線的存放庫，然後選擇 [複製]  。

      ![從 Visual Studio 產生的 [連線到專案] 對話方塊](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > 您在清單方塊中看到的內容，取決於您有權存取的 Azure DevOps 存放庫。

1. 當 Visual Studio 複製您的存放庫之後，[Team Explorer] 即會關閉，而 [方案總管] 即會開啟。 隨即出現一則訊息，指出「按一下上方的 [解決方案與資料夾] 可檢視解決方案清單」  。 選擇 [解決方案與資料夾]  。

      ![Visual Studio 中來自 [Team Explorer] 的「解決方案與資料夾」通知](./media/open-proj-repo-solutions-folders.png)

   解決方案檔 (具體來說為 .sln 檔案) 將會出現在 [解決方案與資料夾] 飛出功能表中。 選擇它，而 Visual Studio 會開啟您的解決方案。

   如果您的存放庫中沒有解決方案檔，飛出功能表將顯示「找不到任何解決方案」。 不過，您可以從資料夾功能表中按兩下任一檔案，以便在 Visual Studio 程式碼編輯器中開啟該檔案。

::: moniker-end

::: moniker range="vs-2019"

1. 開啟 Visual Studio 2019。

1. 在開始視窗中，選擇 [複製或簽出程式碼]  。

   ![檢視 [建立新專案] 視窗](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. 在 [瀏覽存放庫]  區段中，選擇 [Azure DevOps]  。

   ![檢視 [複製或簽出程式碼] 視窗](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   如果您看到登入視窗，請登入您的帳戶。

1. 在 [連線到專案]  對話方塊中，選擇您想要連線的存放庫，然後選擇 [複製]  。

      ![從 Visual Studio 產生的 [連線到專案] 對話方塊](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > 您在清單方塊中看到的內容，取決於您有權存取的 Azure DevOps 存放庫。

   Visual Studio 會開啟 [Team Explorer]  ，並在複製完成時顯示通知。

     ![完成複製後的 Visual Studio [Team Explorer] 視窗](./media/vs-2019/clone-complete-azure-devops.png)

1. 若要檢視您的資料夾和檔案，請選擇 [顯示資料夾檢視]  連結。

     ![完成複製後，Visual Studio [Team Explorer] 視窗的 [解決方案] 區段](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio 會開啟 [方案總管]  。

1. 選擇 [解決方案與資料夾]  連結，搜尋要開啟的解決方案檔 (具體來說為 .sln 檔案)。

      ![Visual Studio 中來自 [Team Explorer] 的「解決方案與資料夾」通知](./media/open-proj-repo-solutions-folders.png)

   如果您的存放庫中沒有解決方案檔，則會顯示「找不到解決方案」的訊息。 不過，您可以從資料夾功能表中按兩下任一檔案，以便在 Visual Studio 程式碼編輯器中開啟該檔案。

::: moniker-end

## <a name="next-steps"></a>後續步驟

如果您已準備好使用 Visual Studio 來撰寫程式碼，請深入了解下列任一個語言特定的教學課程：

- [Visual Studio 教學課程 | **C#** ](./csharp/index.yml)
- [Visual Studio 教學課程 | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio 教學課程 | **C++** ](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio 教學課程 | **Python**](/visualstudio/python/)
- [Visual Studio 教學課程 |**JavaScript**、**TypeScript** 和 **Node.js**](/visualstudio/javascript/)

## <a name="see-also"></a>另請參閱

- [Azure DevOps Services：開始使用 Azure Repos 與 Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn：開始使用 Azure DevOps](/learn/modules/get-started-with-devops/)