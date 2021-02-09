---
title: 快速入門 - 複製 Python 程式碼存放庫
description: 在此快速入門中，您可以使用 Visual Studio Team Explorer 複製 Python Koans 存放庫，以在 Visual Studio 中建立 Python 專案。
ms.date: 12/06/2018
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 55db74b2b2882aac12ac1587c4e972e31f7dfe10
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902401"
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>快速入門：在 Visual Studio 中複製 Python 程式碼的存放庫

[在 Visual Studio 中安裝 Python 支援](installing-python-support-in-visual-studio.md)之後，您可以為 Visual Studio 新增 GitHub 延伸模組。 延伸模組可讓您輕鬆地複製 Python 程式碼的存放庫，並在 IDE 中透過該存放庫建立專案。 您也可以一律在命令列上複製存放庫，然後在 Visual Studio 中使用它們。

## <a name="install-the-github-extension-for-visual-studio"></a>安裝適用於 Visual Studio Code 的 GitHub 延伸模組 \(英文\)。

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

## <a name="work-with-github-in-visual-studio"></a>在 Visual Studio 中使用 GitHub

1. 啟動 Visual Studio。

1. 選取 [ **View**  >  **Team Explorer** ] 以開啟 [ **Team Explorer** ] 視窗，您可以在其中連線至 GitHub 或 Azure Repos，或複製存放庫。 (如果您沒看到如下所示的 [連線] 頁面，請選取最上方工具列上的插頭圖示，它會將您帶到該頁面。)

    ![顯示 Azure Repos、GitHub 和複製存放庫的 Team Explorer 視窗](media/team-explorer.png)

1. 在 [本機 Git 存放庫] 下，選取 [複製] 命令，然後在 URL 欄位中輸入 `https://github.com/gregmalcolm/python_koans`，輸入所複製檔案的資料夾，然後選取 [複製] 按鈕。

    > [!Tip]
    > 您在 **Team Explorer** 中指定的資料夾是接收復制之檔案的確切資料夾。 這與 `git clone` 命令不同，不會在 **Team Explorer** 中建立複製品時，自動使用存放庫名稱建立子資料夾。

1. 當複製完成時，存放庫名稱就會出現在 [本機 Git 存放庫] 清單中。 按兩下該名稱，即可瀏覽至 **Team Explorer** 中的存放庫儀表板。

1. 在 [解決方案] 下，選取 [新增]。

    ![從複製品建立新專案的 Team Explorer 視窗](media/team-explorer-new-project.png)

1. 在出現的 [ **新增專案** ] 對話方塊中，流覽至 **python** 語言 (或搜尋 "Python" ) 、 **從現有的 Python 程式碼** 中選取、指定專案的名稱、將位置設定為與 **存放** 庫相同的資料夾，然後選取 **[確定]**。 在出現的精靈中，選取 [完成]。

1. 從功能表選取 [ **View**  >  **方案總管**]。

1. 在 [方案總管] 中，展開 **python3** 節點，並以滑鼠右鍵按一下 **contemplate_koans.py**，然後選取 [設定為啟動檔案]。 此步驟會告訴 Visual Studio 在執行專案時應該使用哪個檔案。

1. 從功能表選取 [**專案**  >  **Koans 屬性**]，選取 [**一般**] 索引標籤，然後將 **工作目錄** 設定為 "python3"。 因為 Visual Studio 預設會將工作目錄設定為專案根目錄，而非啟動檔案的位置 (*python3\contemplate_koans.py*，而您也可以在專案屬性中看到它)，所以這是必要步驟。 程式碼會在工作資料夾中尋找 *koans.txt* 檔案。因此，如果未變更此值，就會出現執行階段錯誤。

    ![設定 Python 專案的工作目錄](media/projects-set-working-directory.png)

1. 按下 **Ctrl** + **F5** 或選取 [ **Debug**  >  **啟動但不進行調試** 程式] 以執行程式。 如果您看到 *koans.txt* 的 **FileNotFoundError**，請重新檢查上一個步驟中所述的工作目錄設定。

1. 程式順利執行時，會在 *python3/koans/about_asserts.py* 的第 17 行顯示判斷提示錯誤。 這是故意的：程式設計成讓您更正所有故意性錯誤來教導 Python。 (在 Python Koans 所產生的 [Ruby Koans](https://rubykoans.com/) 上可以找到詳細資料)。

    ![Python Koans 程式中的第一個輸出](media/koans-output.png)

1. 開啟 *python3/koans/about_asserts.py*，方法是在 [方案總管] 中巡覽到它，並按兩下該檔案。 請注意，根據預設，在編輯器中看不到行號。 若要變更此選項，請選取 [**工具**  >  **選項**]，選取對話方塊底部的 [**顯示所有設定**]，然後流覽至 [**文字編輯器**  >  **Python**  >  **一般**]，然後選取 [**行號**]：

    ![開啟 Python 檔案的行號](media/options-general-line-numbers.png)

1. 將第 17 行的 `False` 引數變更為 `True`，以更正錯誤。 該行應該如下：

    ```python
    self.assertTrue(True) # This should be True
    ```

1. 再次執行程式。 如果 Visual Studio 警告您發生錯誤，請回應 [是] 以繼續執行程式碼。 接著，您會看到第一次檢查通過，而且程式停止於下一個 Koan。 繼續更正錯誤，並視需要再次執行程式。

> [!Important]
> 在此快速入門中，您已在 GitHub 上建立 *python_koans* 存放庫的直接複製品。 這類存放庫是由其作者保護無法直接變更，因此嘗試將變更認可至存放庫會失敗。 在實務上，開發人員會改為將這類存放庫分支到其自有 GitHub 帳戶，在該處進行變更，然後建立提取要求以將那些變更提交至原始存放庫。 當您有自己的分支時，請使用其 URL，而不是稍早使用的原始存放庫 URL。

## <a name="next-steps"></a>下一步

> [!div class="nextstepaction"]
> [教學課程：在 Visual Studio 中使用 Python](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>另請參閱

- [手動識別現有的 Python 解譯器](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [如何在 Windows 上的 Visual Studio 中安裝 Python 支援](installing-python-support-in-visual-studio.md)
- [安裝位置](installing-python-support-in-visual-studio.md#install-locations)
