---
title: 教學課程：在 Visual Studio 2019 的存放庫中開啟專案
description: 瞭解如何使用 Visual Studio 2019，在 Git 或 Azure DevOps 存放庫中開啟專案。
ms.custom: get-started
ms.date: 01/25/2021
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
monikerRange: vs-2019
ms.openlocfilehash: b7197f9e21bb136f8444170dc8d62341b3b0c07d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886661"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>教學課程：從存放庫開啟專案

在本教學課程中，您將第一次使用 Visual Studio 連線到存放庫，然後從中開啟專案。

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads)頁面免費進行安裝。

## <a name="open-a-project-from-a-github-repo"></a>從 GitHub 存放庫開啟專案

如何使用 Visual Studio 2019 開啟 GitHub 存放庫中的專案，取決於您擁有的版本。 具體而言，如果您已安裝 [**16.8**](/visualstudio/releases/2019/release-notes/) 版或更新版本，您可以 [在 Visual Studio 中](../ide/git-with-visual-studio.md) 找到新的、更全面整合的 Git 體驗。

但無論您安裝的版本為何，您一律可以使用 Visual Studio 從 GitHub 存放庫開啟專案。

#### <a name="168-and-later"></a>[16.8 和更新版本](#tab/vs168later)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>複製 GitHub 存放庫，然後開啟專案

1. 開啟 Visual Studio 2019。

1. 在 [開始] 視窗中，選取 [ **複製存放庫**]。

   ![[複製存放庫] 對話方塊的螢幕擷取畫面，位於 Visual Studio 2019 16.8 版和更新版本中](../ide/media/vs-2019/clone-repository.png)

1. 輸入或鍵入存放庫位置，然後選取 [ **複製**]。

   ![[複製存放庫] 對話方塊的螢幕擷取畫面，其中您會在 Visual Studio 2019 16.8 版和更新版本中輸入 Git 存放庫 URL](../ide/media/vs-2019/clone-repository-enter-location.png)

1. 系統可能會要求您在 [ **Git 使用者資訊** ] 對話方塊中使用您的使用者登入資訊。 您可以新增資訊或編輯其所提供的預設資訊。

   ![[Git 使用者資訊] 對話方塊的螢幕擷取畫面，您可以在 Visual Studio 2019 16.8 版和更新版本中輸入或編輯您的帳戶資訊。](../ide/media/vs-2019/git-user-information-dialog.png)

    選取 [ **儲存** ]，將資訊新增至 .gitconfig 儲存檔案。  (或，您可以稍後選取 [ **取消**] 來選擇是否要這麼做。 ) 

    接著，Visual Studio 會自動從儲存機制載入並開啟方案。

   ![Git 中的專案螢幕擷取畫面，已在 Visual Studio 2019 16.8 版和更新版本的方案總管中開啟](../ide/media/vs-2019/git-solution-explorer.png )

1. 如果您的存放庫包含多個解決方案，您將會在方案總管中看到它們。 您可以選取方案總管中的 [ **切換視圖** ] 按鈕，以查看解決方案清單。

   ![Git 中以方案總管開啟的專案螢幕擷取畫面，其中已醒目提示 Visual Studio 2019 16.8 版和更新版本中的 [切換視圖] 按鈕](../ide/media/vs-2019/git-solution-explorer-switch-views.png)

   方案總管接著會提供選項，讓您在 **資料夾檢視** 中開啟根資料夾，或選取要開啟的方案檔。

   ![當您在 Visual Studio 2019 16.8 版和更新版本中選取 [切換視圖] 按鈕之後，在方案總管中開啟之 Git 檔案的螢幕擷取畫面](../ide/media/vs-2019/git-solution-explorer-view-solution.png)

    若要切換視圖，請再次選取 [ **切換視圖** ] 按鈕。

    > [!TIP]
    > 您也可以使用 Visual Studio IDE 中的 **Git** 功能表來複製存放庫，並開啟專案。
    >
    > ![Visual Studio 2019 16.8 版和更新版本中 Git 功能表的螢幕擷取畫面](../ide/media/vs-2019/git-menu-clone-create-git-repository.png)

#### <a name="open-a-project-locally-from-a-previously-cloned-github-repo"></a>從先前複製的 GitHub 存放庫在本機開啟專案

1. 開啟 Visual Studio 2019。

1. 在 [開始] 視窗中，選取 [ **開啟專案或方案**]。

    Visual Studio 會開啟檔案總管的實例，您可以在其中流覽至您的方案或專案，然後選取它來開啟它。

   ![在 Visual Studio 2019 16.8 版和更新版本中，[開啟專案或方案] 視窗的螢幕擷取畫面](../ide/media/vs-2019/open-local-project-from-cloned-repo.png)

    如果您最近開啟專案或方案，請從 [ **最近開啟** ] 區段中選取該專案或方案，以快速地將其開啟。

    > [!TIP]
    > 您也可以使用 Visual Studio IDE 中的 **Git** 功能表，從您先前複製的存放庫開啟本機資料夾和檔案。
    >
    > ![Visual Studio 2019 16.8 版和更新版本中 Git 功能表的螢幕擷取畫面，其中已展開本機存放庫選項](../ide/media/vs-2019/git-menu-local-repositories.png)


    開始撰寫程式碼！

#### <a name="167-and-earlier"></a>[16.7 及更早版本](#tab/vs167earlier)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>複製 GitHub 存放庫，然後開啟專案

1. 開啟 Visual Studio 2019。

1. 在 [開始] 視窗中，選取 [ **複製或簽出程式碼**]。

   ![[建立新專案] 視窗的螢幕擷取畫面，在 Visual Studio 2019 16.7 版及更早版本中](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. 輸入或鍵入存放庫位置，然後選取 [ **複製**]。

   ![Visual Studio 2019 16.7 版及更早版本中 [複製或簽出程式碼] 視窗的螢幕擷取畫面](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio 從存放庫開啟專案。

1. 如果您有可用的解決方案檔，它將會出現在 [解決方案與資料夾] 飛出功能表中。 選取它，Visual Studio 就會開啟您的解決方案。

   ![Visual Studio 2019 16.7 版及更早版本中的 [方案總管] 下拉式清單的螢幕擷取畫面](./media/open-proj-repo-github-solutions-folders-picker.png)

   如果您沒有解決方案檔 (具體而言，您的存放庫中) .sln 檔案，則飛出功能表會顯示「找不到任何解決方案」。 不過，您可以從資料夾功能表中按兩下任一檔案，以便在 Visual Studio 程式碼編輯器中開啟該檔案。

    開始撰寫程式碼！

---

## <a name="connect-to-an-azure-devops-server"></a>連接到 Azure DevOps 伺服器

當您使用 Visual Studio 2019 連接到 Azure DevOps 伺服器時所看到的內容，取決於您擁有的版本。 具體而言，如果您已安裝 [**16.8**](/visualstudio/releases/2019/release-notes/) 版或更新版本，我們已變更 UI，以配合 Visual Studio 中 Visual Studio 的全新、更全面整合的 [Git 體驗](../ide/git-with-visual-studio.md) 。

但是無論您已安裝哪一個版本，一律可以使用 Visual Studio 連接到 Azure DevOps 伺服器。

#### <a name="168-and-later"></a>[16.8 和更新版本](#tab/vs168later)

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

#### <a name="167-and-earlier"></a>[16.7 及更早版本](#tab/vs167earlier)

1. 開啟 Visual Studio 2019。

1. 在 [開始] 視窗中，選取 [ **複製或簽出程式碼**]。

   ![[建立新專案] 視窗的螢幕擷取畫面，在 Visual Studio 2019 16.7 版及更早版本中](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. 在 [ **流覽存放庫]** 區段中，選取 [ **Azure DevOps**]。

   ![[複製或簽出程式碼] 視窗的螢幕擷取畫面，其中會列出 Visual Studio 2019 16.7 版及更早版本中 Azure DevOps 的 [流覽儲存機制] 區段](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   如果您看到登入視窗，請登入您的帳戶。

1. 在 [ **連接到專案** ] 對話方塊中，選擇您要連接的存放庫，然後選取 [ **複製**]。

      ![[連線到專案] 對話方塊的螢幕擷取畫面，此對話方塊是從 Visual Studio 2019 16.7 版及更早版本所產生](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > 您在清單方塊中看到的內容，取決於您有權存取的 Azure DevOps 存放庫。

   Visual Studio 會開啟 [Team Explorer]，並在複製完成時顯示通知。

     ![複製完成之後，Visual Studio 2019 16.7 版及更早版本中 Team Explorer 視窗的螢幕擷取畫面](./media/vs-2019/clone-complete-azure-devops.png)

1. 若要查看您的資料夾和檔案，請選取 [ **顯示資料夾視圖** ] 連結。

     ![在複製完成之後，Visual Studio 2019 16.7 版及更早版本中，[Team Explorer] 視窗的 [解決方案] 區段螢幕擷取畫面](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio 會開啟 [方案總管]。

1. 選擇 [ **方案和資料夾** ] 連結，以搜尋解決方案檔 (具體而言，就是開啟) 的 .sln 檔案。

      ![Visual Studio 2019 16.7 版及更早版本中 Team Explorer 的「解決方案和資料夾」通知螢幕擷取畫面](./media/open-proj-repo-solutions-folders.png)

   如果您的存放庫中沒有解決方案檔，則會出現「找不到任何解決方案」訊息。 不過，您可以從資料夾功能表中按兩下任一檔案，以便在 Visual Studio 程式碼編輯器中開啟該檔案。

---

## <a name="next-steps"></a>下一步

如果您已準備好使用 Visual Studio 來撰寫程式碼，請深入了解下列任一個語言特定的教學課程：

- [Visual Studio 教學課程 | **C #**](./csharp/index.yml)
- [Visual Studio 教學課程 | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio 教學課程 | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio 教學課程 | **Python**](../python/index.yml)
- [Visual Studio 教學課程 |**JavaScript**、**TypeScript** 和 **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>另請參閱

- [Visual Studio 中新的 Git 體驗](../ide/git-with-visual-studio.md)
- [Azure DevOps Services：開始使用 Azure Repos 和 Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn：開始使用 Azure DevOps](/learn/modules/get-started-with-devops/)