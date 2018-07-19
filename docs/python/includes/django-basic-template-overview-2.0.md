---
ms.topic: include
ms.openlocfilehash: 0ee0234e91cdf07c2b52c39d065d527a776dc4ce
ms.sourcegitcommit: 64bf371ffe294e9b3cf769db03cf0f5c1a9b680c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2018
ms.locfileid: "35666975"
---
### <a name="create-a-project-using-django-20"></a>使用 Django 2.0 建立專案

目前，「空白 Django Web 專案」範本使用最新的 Django 1.x 版。 若要使用 Django 2.x，最快的方法是將 Django 2.x 檔案匯入至 Django 1.x 專案。 依照上述程序進行，您可以利用由 Visual Studio 專案範本處理的其他詳細資料。

1. 使用上節所述的「空白 Django Web 專案」範本來建立 Django 1.x 專案。 不過，請在看到「此專案需要外部相依性」提示時，選取 [我將自行安裝]。 選擇此選項，可讓您避免安裝會在稍後步驟中解除安裝的相依性。

1. 開啟命令提示字元，然後瀏覽至暫存資料夾。

1. 執行 `pip install django` 以在全域 Python 環境中安裝最新的 Django 套件。

1. 執行 `django-admin startproject <project_name>` 以在步驟 1 使用的相同專案名稱來取代 `<project_name>`，例如 "HelloDjango"。 `startproject` 命令會建立 `manage.py` 檔案以及符合 `<project_name>` 的資料夾，其中包含 `__init__.py`、`settings.py`、`urls.py` 及 `wsgi.py` 檔案。

1. 在 Visual Studio 中，以 Django 2.x 檔案取代專案中的 Django 1.x 檔案，如下所示：

  a. 在 [方案總管] 中，刪除 `manage.py` 與 Django 應用程式資料夾。
  b. 以滑鼠右鍵按一下專案，選取 [加入] > [現有項目...] 命令，瀏覽並選取步驟 4 中建立的 `manage.py` 檔案，然後選取 [確定]。 Visual Studio 接著會將該檔案複製到專案中。
  c.  再次以滑鼠右鍵按一下專案，選取 [加入] > [現有資料夾...] 命令，瀏覽並選取步驟 4 中建立的應用程式資料夾，然後選取 [確定]。 Visual Studio 接著會將整個資料夾與其四個檔案複製到專案中。
  d. 以滑鼠右鍵按一下 `manage.py`，然後選取 [設定為啟動檔案]。

  > [!Important]
  > Visual Studio 專案中顯示的應用程式名稱必須符合與 `django-admin` 公用程式一起使用的 `<project_name>`，原因是公用程式會使用該名稱作為 Python 程式碼檔案內的命名空間。

1. 開啟 `requirements.txt`，將其內容變更為 `django >=2.0, <3`，然後儲存該檔案。

1. 在 [方案總管] 中的 [Python 環境] 節點上按一下滑鼠右鍵，然後選取 [新增虛擬環境...]。接受所出現對話方塊中的預設值，然後選取 [建立]。 接受所有的系統管理員權限提示。