---
title: "快速入門 - 在 Visual Studio 中使用範本來建立 Python 專案 | Microsoft Docs"
description: "使用內建範本之一來建立 Visual Studio 專案，以快速開始使用 Python。"
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 2af5a7412b6d4a6554d4bc11f5877541a3384115
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>快速入門：在 Visual Studio 中從範本建立 Python 專案

[在 Visual Studio 2017 中安裝 Python 支援](installing-python-support-in-visual-studio.md)之後，就可以使用各種範本輕鬆地建立新的 Python 專案。

1. 啟動 Visual Studio。

1. 選取 [檔案] > [新增] > [專案] (Ctrl+Shift+N)。 在 [新增專案] 對話方塊中，搜尋 "Python"，然後選取您想要的範本。 請注意，選取範本時會顯示範本所提供項目的簡短描述  (另請參閱 [Python 專案](managing-python-projects-in-visual-studio.md#project-templates))。

    ![含 Python 範本的 VS2017 [新增專案] 對話方塊](media/projects-new-project-dialog2.png)

1. 在本快速入門中，選取 [Python 應用程式] 範本，並提供專案的名稱 (例如 "MakePI") 和位置，然後選取 [確定]。

1. Visual Studio 會建立專案檔 (磁碟上的 `.pyproj` 檔案) 以及範本所述的任何其他檔案。 使用 [Python 應用程式] 範本，專案只會包含一個名稱與您專案相同的空白檔案。 根據預設，會在 Visual Studio 編輯器中開啟檔案。

    ![使用 Python 應用程式範本時所產生的專案](media/projects-new-structure.png)

1. 將某個程式碼新增至開啟的檔案，例如計算並顯示 1000 個位數的 PI 的下面程式碼：

    ```python
    """ Print digits of PI; code adapted from the second, shorter solution
    at http://www.codecodex.com/wiki/Calculate_digits_of_pi#Python
    """

    from time import perf_counter

    def pi_digits_Python(digits):
        scale = 10000
        maxarr = int((digits / 4) * 14)
        arrinit = 2000
        carry = 0
        arr = [arrinit] * (maxarr + 1)
        output = ""

        for i in range(maxarr, 1, -14):
            total = 0
            for j in range(i, 0, -1):
                total = (total * j) + (scale * arr[j])
                arr[j] = total % ((j * 2) - 1)
                total = total / ((j * 2) - 1)

            output += "%04d" % (carry + (total / scale))
            carry = total % scale

        return output;

    def test_py():
        digits = 1000;

        start = perf_counter()
        output = pi_digits_Python(digits);
        elapsed = perf_counter() - start;

        print("PI to " + str(digits) + " digits in " + str(int(elapsed * 10000)/10000) + " seconds:")

        ## replace inserts the decimal point
        print(output.replace("3", "3.", 1))

    if __name__ == "__main__":
        test_py();
    ```

1. 按 Ctrl+F5，或是選取功能表上的 [偵錯] > [啟動但不偵錯]，以執行程式。 結果會顯示在主控台視窗中。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [教學課程：在 Visual Studio 中使用 Python](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>另請參閱

- [建立現有 Python 解譯器的環境](managing-python-environments-in-visual-studio.md#creating-an-environment-for-an-existing-interpreter)。
- [在 Visual Studio 2015 和更早版本中安裝 Python 支援](installing-python-support-in-visual-studio.md)。
- [安裝位置](installing-python-support-in-visual-studio.md#install-locations)。
