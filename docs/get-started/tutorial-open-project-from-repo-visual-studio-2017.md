---
title: 教學課程：在 Visual Studio 2017 的存放庫中開啟專案
description: 瞭解如何使用 Visual Studio 2017，在 Git 或 Azure DevOps 存放庫中開啟專案。
ms.custom: vs-acquisition, get-started
ms.date: 02/15/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
monikerRange: vs-2017
ms.openlocfilehash: 5543a568f7246d9600ba375d9a1cf19af4cbd2d4
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389198"
---
# <a name="tutorial-open-a-project-from-a-repo-in-visual-studio-2017"></a>教學課程：在 Visual Studio 2017 的存放庫中開啟專案

在本教學課程中，您將使用 Visual Studio 2017 來第一次連線至存放庫，然後從中開啟專案。

> [!TIP]
> 有一個全新、更緊密整合的方式，可與 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)中的 GitHub 存放庫進行連接。 如需詳細資訊，請參閱 [**Visual Studio 2019 頁面中的新 Git 體驗**](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true) 。

## <a name="open-a-project-from-a-github-repo-by-using-visual-studio-2017"></a>使用 Visual Studio 2017 開啟 GitHub 存放庫中的專案

1. 開啟 Visual Studio 2017。

1. 從頂端功能表列中 **，選取 [**  >    >  **從原始檔控制** 開啟檔案]。

   [Team Explorer - 連接] 窗格隨即開啟。

    ![Visual Studio IDE 中的 [Team Explorer] 視窗](./media/open-proj-repo-team-explorer.png)

1. 在 [ **本機 Git 存放庫** ] 區段中，選取 [ **複製**]。

    ![從 [本機 Git 存放庫] 區段中選擇 [複製]](./media/open-proj-repo-local-git-repo-clone.png)

1. 在 [**輸入要複製的 Git** 存放庫 url] 方塊中，輸入或貼上存放庫的 url，然後按 _ * Enter * *。 (您可能會看見登入 GitHub 的提示；如果看見提示，請登入)。

   當 Visual Studio 複製您的存放庫之後，[Team Explorer] 即會關閉，而 [方案總管] 即會開啟。 隨即出現一則訊息，指出「按一下上方的 [解決方案與資料夾] 可檢視解決方案清單」。 選擇 [解決方案與資料夾]。

   ![從 [方案總管] 中選擇 [解決方案與資料夾]](./media/open-proj-repo-github-solutions-folders.png)

1. 如果您有可用的解決方案檔，它將會出現在 [解決方案與資料夾] 飛出功能表中。 選擇它，而 Visual Studio 會開啟您的解決方案。

   ![選擇您想要從 [方案總管] 下拉式清單中開啟的解決方案](./media/open-proj-repo-github-solutions-folders-picker.png)

   如果您的存放庫中沒有解決方案檔 (具體來說為 .sln 檔案)，飛出功能表將顯示「找不到任何解決方案」。 不過，您可以從資料夾功能表中按兩下任一檔案，以便在 Visual Studio 程式碼編輯器中開啟該檔案。

### <a name="review-your-work"></a>檢閱工作

檢視以下動畫以檢查您在上一節中完成的工作。

   ![使用 Visual Studio 在 GitHub 存放庫中開啟專案的動畫](./media/open-project-from-github.gif)

> [!NOTE]
> 如需 Visual Studio 2019 的特定資訊，請參閱 [Visual Studio 2019 頁面中的從存放庫開啟專案](tutorial-open-project-from-repo-visual-studio-2019.md) 。

## <a name="open-a-project-from-an-azure-devops-repo-by-using-visual-studio-2017"></a>使用 Visual Studio 2017 開啟 Azure DevOps 存放庫中的專案

1. 開啟 Visual Studio 2017。

1. 從頂端功能表列中 **，選取 [**  >    >  **從原始檔控制** 開啟檔案]。

   [Team Explorer - 連接] 窗格隨即開啟。

    ![Visual Studio IDE 中的 [Team Explorer] 視窗](./media/open-proj-repo-team-explorer.png)

1. 以下是兩種可連線到您 Azure DevOps 存放庫的方式：

      - 在 [ **託管服務提供者** ] 區段中，選取 **[連接 ...]**。

        ![Visual Studio IDE 內 [Team Explorer] 視窗的 [託管服務提供者] 區段](./media/open-proj-repo-azure-devops.png)

      - 在 [ **管理連接** ] 下拉式清單中，選取 **[連接到專案 ...]**。

        ![Visual Studio IDE 內 [Team Explorer] 視窗的 [管理連線] 區段](./media/open-proj-repo-azuredevops-manage-connections.png)

1. 在 [ **連接到專案** ] 對話方塊中，選擇您要連接的存放庫，然後選取 [ **複製**]。

      ![從 Visual Studio 產生的 [連接到專案] 對話方塊](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > 您在清單方塊中看到的內容，取決於您有權存取的 Azure DevOps 存放庫。

1. 當 Visual Studio 複製您的存放庫之後，[Team Explorer] 即會關閉，而 [方案總管] 即會開啟。 隨即出現一則訊息，指出「按一下上方的 [解決方案與資料夾] 可檢視解決方案清單」。 選擇 [解決方案與資料夾]。

      ![Visual Studio 中來自 [Team Explorer] 的「解決方案與資料夾」通知](./media/open-proj-repo-solutions-folders.png)

   解決方案檔 (具體來說為 .sln 檔案) 將會出現在 [解決方案與資料夾] 飛出功能表中。 選擇它，而 Visual Studio 會開啟您的解決方案。

   如果您的存放庫中沒有解決方案檔，飛出功能表將顯示「找不到任何解決方案」。 不過，您可以從資料夾功能表中按兩下任一檔案，以便在 Visual Studio 程式碼編輯器中開啟該檔案。

## <a name="next-steps"></a>後續步驟

如果您已準備好使用 Visual Studio 2017 來撰寫程式碼，請深入瞭解下列任何特定語言的教學課程：

- [Visual Studio 教學課程 | **C #**](./csharp/index.yml)
- [Visual Studio 教學課程 | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio 教學課程 | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio 教學課程 | **Python**](../python/index.yml)
- [Visual Studio 教學課程 |**JavaScript**、**TypeScript** 和 **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 2019 的存放庫中開啟專案](tutorial-open-project-from-repo-visual-studio-2019.md)
- [Visual Studio 2019 中的新 Git 體驗](../ide/git-with-visual-studio.md)
- [Azure DevOps Services：開始使用 Azure Repos 和 Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn：開始使用 Azure DevOps](/learn/modules/get-started-with-devops/)
