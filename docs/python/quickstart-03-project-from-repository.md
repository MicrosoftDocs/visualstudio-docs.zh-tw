---
title: "快速入門：在 Visual Studio 中複製 Python 程式碼的存放庫 | Microsoft Docs"
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1ce09377-9073-404c-9339-fa871a4b0841
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 8ba37a922c24a02d7586b9c95f57ad27a7152736
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>快速入門：在 Visual Studio 中複製 Python 程式碼的存放庫

[在 Visual Studio 2017 中安裝 Python 支援](installation.md)之後，就可以輕鬆地複製 Python 程式碼的存放庫，並從中建立專案。

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

2. 啟動 Visual Studio。

3. 選取 [檢視] > [Team Explorer] 以開啟 [Team Explorer] 視窗，您可以從中連線到 GitHub 或 Visual Studio Team Services，或是複製存放庫。

    ![顯示 Visual Studio Team Services 和 GitHub 並複製存放庫的 Team Explorer 視窗](media/team-explorer.png)

4. 在 [本機 Git 存放庫] 的 [URL] 欄位中，輸入 `https://github.com/gregmalcolm/python_koans`，並輸入所複製檔案的資料夾，然後選取 [複製]。

    > [!Tip]
    > 您在 Team Explorer 中指定的資料夾是用來接收所複製檔案的特定資料夾。 不同於 `git clone` 命令，在 Team Explorer 中建立複製品不會自動使用存放庫的名稱來建立子資料夾。

5. 複製完成時，請按兩下 Team Explorer 底部的存放庫資料夾，以巡覽至存放庫儀表板。 在 [方案] 下，選取 [新增]。

    ![從複製品建立新專案的 Team Explorer 視窗](media/team-explorer-new-project.png)

6. 在出現的 [新增專案] 對話方塊中，選取 [從現有 Python 程式碼]，並指定專案名稱，再將 [位置] 設定為與存放庫相同的資料夾，然後選取 [確定]。 在出現的精靈中，選取 [完成]。

7. 從功能表中選取 [檢視] > **方案總管**。

8. 在方案總管中，展開 `python3` 節點，並以滑鼠右鍵按一下 `contemplate_koans.py`，然後選取 [設定為啟動檔案]。 此步驟會告訴 Visual Studio 在執行專案時應該使用哪個檔案。

9. 從功能表中選取 [專案] > [屬性]，並選取 [一般] 索引標籤，然後將 [工作目錄] 設定為 [python3]。 根據預設，因為 Visual Studio 將工作目錄設定為專案根目錄，而非啟動檔案的位置 (`python3\contemplate_koans.py`，而您也可以在專案屬性中看到它)，所以這是必要的。 程式碼會在工作資料夾中尋找 `koans.txt` 檔案，因此不需要變更此值，您就會看到執行階段錯誤。

    ![設定 Python 專案的工作目錄](media/projects-set-working-directory.png)

10. 按 Ctrl + F5，或是選取 [偵錯] > [啟動但不偵錯]，以執行程式。 如果您看到 `koans.txt` 的 `FileNotFoundError`，請重新檢查上一個步驟中的工作目錄設定。

11. 程式順利執行時，會在 `python3/koans/about_asserts.py` 的第 17 行顯示判斷提示錯誤。 這是故意的：程式設計成讓您更正所有故意性錯誤來教導 Python。 (在 Python Koans 所產生的 [Ruby Koans](http://rubykoans.com/) 上可以找到詳細資料)。

    ![Python Koans 程式中的第一個輸出](media/koans-output.png)

12. 開啟 `python3/koans/about_asserts.py`，方法是在方案總管中巡覽到它，並按兩下檔案。 請注意，根據預設，在編輯器中看不到行號。 若要變更這個作業，請選取 [工具] > [選項]，並選取對話方塊底部的 [顯示所有設定]，再巡覽至 [文字編輯器] > [Python] > [一般]，然後選取 [行號]：

    ![開啟 Python 檔案的行號](media/options-general-line-numbers.png)

13. 將第 17 行的 `False` 引數變更為 `True`，以更正錯誤。 該行應該如下：

    ```python
    self.assertTrue(True) # This should be True
    ```

14. 重新執行程式，以確認第一次檢查通過，而且程式停止於下一個 Koan。 繼續更正錯誤，並視需要重新執行程式。

> [!Important]
> 在本快速入門中，您已在 GitHub 上建立 *python_koans* 存放庫的直接複製品。 這類存放庫是由其作者保護無法直接變更，因此嘗試將變更認可至存放庫會失敗。 在實務上，開發人員會改為將這類存放庫分叉到其專屬 GitHub 帳戶，並在該處進行變更，然後建立提取要求，將這些變更提交至原始存放庫。 [教學課程步驟 6 - 使用 Git](vs-tutorial-01-06.md) 會描述下列步驟。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [教學課程：在 Visual Studio 中使用 Python](vs-tutorial-01-01.md)

## <a name="see-also"></a>另請參閱

- [建立現有 Python 解譯器的環境](python-environments.md#creating-an-environment-for-an-existing-interpreter)。
- [在 Visual Studio 2015 和更早版本中安裝 Python 支援](installation.md).
- [安裝位置](installation.md#install-locations).
