---
title: 使用 requirements.txt 檔案管理套件需求
description: requirements.txt 檔案會描述專案的相依性。 如果您收到包含 requirements.txt 檔案的專案，就可以輕鬆地在單一步驟中安裝那些相依性。
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 49f87ff5836188d6fefb80feac94b27902de7968
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2018
ms.locfileid: "50218418"
---
# <a name="manage-required-packages-with-requirementstxt"></a>使用 requirements.txt 管理必要套件

如果您與其他人共用專案、使用建置系統，或是打算將專案複製到需要還原環境的其他任何位置，則必須指定專案所需的外部套件。 建議的方法是使用 [requirements.txt 檔案](http://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org)，此檔案包含 pip 命令清單，可安裝所需的相依套件版本。 最常見的命令是 `pip freeze > requirements.txt`，它會將環境的目前套件清單記錄到 *requirements.txt*。

就技術而言，任何檔案名稱都可用來追蹤必要條件 (透過在安裝套件時使用 `-r <full path to file>`)，但 Visual Studio 為 *requirements.txt* 提供了專屬支援：

- 若您已載入包含 *requirements.txt* 的專案，並想要安裝該檔案中列出的所有套件，請展開 [方案總管] 中的 [Python 環境] 節點，然後以滑鼠右鍵按一下環境節點，並選取 [從 requirements.txt 安裝]：

    ![Install from requirements.txt (從 requirements.txt 安裝)](media/environments-requirements-txt-install.png)

- 若您已在環境中安裝所有必要套件，可以在 [方案總管] 中的環境上按一下滑鼠右鍵，然後選取 [產生 requirements.txt] 以建立必要的檔案。 如果該檔案已經存在，系統會提示您如何更新它：

    ![更新 requirements.txt 選項](media/environments-requirements-txt-replace.png)

  - [Replace entire file (取代整個檔案)] 會移除所有已存在的項目、註解及選項。
  - [重新整理現有項目] 會偵測套件需求並更新版本規範，以符合您目前已安裝的版本。
  - [Update and add entries (更新及新增項目)] 會重新整理所找到的任何需求，並將所有其他套件新增到檔案結尾。

由於 *requirements.txt* 檔案的用意是要固定住環境的需求，因此所有安裝的套件都已寫明精確的版本。 使用精確的版本可確保您可以在另一部電腦上輕鬆重現您的環境。 即使安裝套件時已指定版本範圍，仍然會包含這些套件作為另一個套件的相依性，或隨附於 pip 以外的安裝程式。

如果套件是 pip 無法安裝的套件，並且出現在 *requirements.txt* 檔案中，整個安裝就會失敗。 在此情況下，請手動編輯檔案以將此套件排除，或使用 [pip 的選項](https://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format)來參考該套件的可安裝版本。 例如，您可能偏好使用 [`pip wheel`](https://pip.readthedocs.org/en/latest/reference/pip_wheel.html) 來編譯相依性並將 `--find-links <path>` 選項新增到您的 *requirements.txt*：

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中管理 Python 環境](managing-python-environments-in-visual-studio.md)
- [選取專案的解譯器](selecting-a-python-environment-for-a-project.md)
- [搜尋路徑](search-paths.md)
- [Python 環境視窗參考](python-environments-window-tab-reference.md)
