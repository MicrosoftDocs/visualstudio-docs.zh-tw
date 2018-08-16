---
ms.topic: include
ms.openlocfilehash: ff6523d33e29f4fcc6fd02c08e0a35ac00892829
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638387"
---
### <a name="create-a-project-using-django-20"></a>使用 Django 2.0 建立專案

目前 **空白 Django Web 專案**範本使用最新的 Django 1.x 版。 若要使用 Django 2.x，最快的方法是將 Django 2.x 檔案匯入 Django 1.x 專案。 依照上述程序進行，您可以利用由 Visual Studio 專案範本處理的其他詳細資料。

1. 使用上節所述的**空白 Django Web 專案**範本，建立 Django 1.x 專案。 但在出現 [This project requires external dependencies] (此專案需要外部相依性) 提示時選取 [I will install them myself] (自行安裝)。 選擇此選項，可讓您避免安裝會在稍後步驟中解除安裝的相依性。

1. 開啟命令提示字元，然後瀏覽至暫存資料夾。

1. 執行 `pip install django` 以在全域 Python 環境中安裝最新的 Django 套件。

1. 執行 `django-admin startproject <project_name>` 以在步驟 1 使用的相同專案名稱來取代 `<project_name>`，例如 "HelloDjango"。 `startproject` 命令會依據 `<project_name>` 建立 *manage.py* 檔案與資料夾，並在其中包含 *\_\_init\_\_.py*、*settings.py*、*urls.py* 及 *wsgi.py* 等檔案。

1. 在 Visual Studio 中，以 Django 2.x 檔案取代專案中的 Django 1.x 檔案，如下所示：

    1. 在 [方案總管] 中，刪除 **manage.py** 與 Django 應用程式資料夾。
    1. 以滑鼠右鍵按一下專案，再選取 [新增]  >  [現有項目] 命令，然後瀏覽並選取在步驟 4 中建立的 **manage.py** 檔案，最後選取 [確定]。 Visual Studio 接著會將該檔案複製到專案中。
    1. 再以滑鼠右鍵按一下專案，接著選取 [新增]  >  [現有資料夾...] 命令，然後瀏覽並選取在步驟 4 中建立的應用程式資料夾，最後選取 [確定]。 Visual Studio 接著會將整個資料夾與其四個檔案複製到專案中。
    1. 以滑鼠右鍵按一下 **manage.py** ，然後選取 [Set as Startup File] (設定為啟動檔案)。

    > [!Important]
    > Visual Studio 專案中顯示的應用程式名稱必須符合與 `django-admin` 公用程式一起使用的 `<project_name>`，原因是公用程式會使用該名稱作為 Python 程式碼檔案內的命名空間。

1. 開啟 *requirements.txt*，並將其內容變更為 `django >=2.0, <3`，然後儲存檔案。

1. 在 [方案總管] 中，以滑鼠右鍵按一下 [Python 環境] 節點，然後選取 [新增虛擬環境]。 接受所出現對話方塊中的預設值，然後選取 [建立]。 接受所有的系統管理員權限提示。