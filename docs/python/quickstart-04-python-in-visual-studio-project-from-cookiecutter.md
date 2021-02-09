---
title: 快速入門-使用 Cookiecutter 建立 Python 專案
description: 在此快速入門中，您可以使用 Cookiecutter 範本來建立 Python 的 Visual Studio 專案。
ms.date: 02/25/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 4c8a3727faa01b69962dd3dc456ac7b704f62882
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902443"
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>快速入門：從 Cookiecutter 範本建立專案

[在 Visual Studio 中安裝 Python 支援](installing-python-support-in-visual-studio.md)之後，就可以從 Cookiecutter 範本輕鬆地建立新專案，包含發佈至 GitHub 的許多專案。 [Cookiecutter (英文)](https://cookiecutter.readthedocs.io/en/latest/) 提供尋找範本、輸入範本選項和建立專案及檔案的圖形化使用者介面。 它隨附於 Visual Studio 2017 和更新版本，並可在舊版的 Visual Studio 中另行安裝。

1. 在本快速入門中，會先安裝 Anaconda3 Python 散發，其中包含這裡所示的 Cookiecutter 範本的必要 Python 套件。 執行 Visual Studio 安裝程式，選取 [ **修改**]，在右側展開 **Python 開發** 的選項，然後選取 [32] 或 [64]) 的 [ **Anaconda3** ] (。 請注意，根據您的網際網路速度，安裝可能需要一些時間，但這是安裝所需套件的最簡單方式。

1. 啟動 Visual Studio。

1.   >    >  **從 Cookiecutter** 選取 [檔案新增]。 此命令會在 Visual Studio 中開啟視窗，而您可以在其中瀏覽範本。

    ![從 Cookiecutter 範本新增專案](media/projects-from-cookiecutter1.png)

1. 選取 [ **Microsoft/python-sklearn-分類器-Cookiecutter** ] 範本，然後選取 **[下一步]**。 (當您第一次使用特定範本時，Visual Studio 會安裝所需 Python 套件，程序可能需要花幾分鐘時間)。

1. 在下一個步驟中，於 [建立位置] 欄位中設定新專案的位置，然後選取 [建立並開啟專案]。

    ![使用 Cookiecutter 的第二個步驟，設定專案屬性](media/projects-from-cookiecutter2.png)

1. 當程式完成時，您會看到「訊息 **已成功使用範本建立** 檔案 ...」。專案會自動在方案總管中開啟。

1. 按下 **Ctrl** + **F5** 或選取 [ **Debug**  >  **啟動但不進行調試** 程式] 以執行程式。

    ![python-sklearn-classifier-cookiecutter 範本專案的輸出](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>下一步

> [!div class="nextstepaction"]
> [教學課程：在 Visual Studio 中使用 Python](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>另請參閱

- [使用 Cookiecutter 延伸模組](using-python-cookiecutter-templates.md)
- [手動識別現有的 Python 解譯器](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [在 Visual Studio 2015 及更早版本中安裝 Python 支援](installing-python-support-in-visual-studio.md)
- [安裝位置](installing-python-support-in-visual-studio.md#install-locations)
