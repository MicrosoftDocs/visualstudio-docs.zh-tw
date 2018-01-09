---
title: "快速入門：使用 Visual Studio 建立您的第一個 Python Web 應用程式 | Microsoft Docs"
ms.custom: 
ms.date: 12/1/2017"
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
ms.devlang: python
author: kraigb
ms.author: kraigb
manager: ghogen
dev_langs: python
ms.workload: python
ms.openlocfilehash: bf0a6e187a98a03d3beed33537fe5244ecd5d35d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="quickstart-use-visual-studio-to-create-your-first-python-web-app"></a>快速入門：使用 Visual Studio 建立您的第一個 Python Web 應用程式

在這個 5-10 分鐘的 Visual Studio 整合式開發環境 (IDE) 簡介中，您要建立簡單的 Python Web 應用程式。 如果您尚未安裝 Visual Studio，請在[這裡](http://www.visualstudio.com)免費安裝它。

## <a name="create-the-project"></a>建立專案

1. 開啟 Visual Studio 2017。

1. 從頂端功能表列，依序選擇 [檔案] > [新增] > [專案]。

1. 在 [新增專案] 對話方塊的左窗格中，展開 [其他語言]，然後選取 [Python]。 在中間窗格中，選擇 [Web 專案]，將專案命名為如 "HelloPython"，然後選擇 [確定]。

    如果您看不到 Python 專案範本，請取消 [新增專案] 對話方塊，然後從頂端功能表列中選擇 [工具] > [Get Tools and Features] (取得工具與功能) 開啟 Visual Studio 安裝程式。 選擇 [Python 開發] 工作負載，然後選擇 [修改]。

    ![Visual Studio 安裝程式中的 Python 開發工作負載](../python/media/installation-python-workload.png)

1. 隨即在**方案總管**右窗格中開啟新專案。 因為專案此時未包含任何其他檔案，所以是空的。

    ![顯示新建立之空專案的方案總管](media/quickstart-python-01-empty-project.png)

## <a name="install-the-falcon-library"></a>安裝 Falcon 程式庫

Python 中的 Web 應用程式幾乎一律使用許多可用的 Python 程式庫之一來處理低階的詳細資料，例如路由 Web 要求和成形回應。 Visual Studio 中的 Python 開發工作負載提供圍繞 Bottle、Flask 和 Django 程式庫而建置的[各種 Web 應用程式範本](../python/template-web.md)。

但在本快速入門中，您要使用不同的程式庫 [Falcon](https://falconframework.org/)，體驗安裝套件以及從頭開始建立 Web 應用程式的過程。 為求簡便，下列步驟會將 Falcon 安裝到預設的全域環境。

1. 請展開專案的 [Python 環境] 節點，以查看專案的預設環境。

    ![顯示預設環境的方案總管](media/quickstart-python-02-default-environment.png)

1. 以滑鼠右鍵按一下環境並選取 [安裝 Python 套件...]。此命令會開啟 [套件] 索引標籤上的 [Python 環境] 視窗。在 [搜尋] 欄位中輸入 "falcon"，並選取 ["pip install falcon" from PyPI] (PyPI 的 "pip 安裝 falcon")。 接受所有的系統管理員權限提示，並觀察 Visual Studio [輸出] 視窗的進度。

    ![安裝 Falcon 程式庫](media/quickstart-python-03-install-package.png)

1. 安裝之後，程式庫會出現在**方案總管**的環境中，這表示您可以在 Python 程式碼中使用它。

    ![已安裝 Falcon 程式庫](media/quickstart-python-04-package-installed.png)

請注意，開發人員不是將程式庫安裝在全域環境中，他們一般會建立「虛擬環境」並在這裡安裝特定專案的程式庫。 Visual Studio 中有許多 Python 專案範本包含 `requirements.txt` 檔案，它會列出範本相依的程式庫。 從這些範本之一建立專案，會觸發建立程式庫安裝所在的虛擬環境。 如需詳細資訊，請參閱 [Python 環境 - 虛擬環境](../python/python-environments.md#virtual-environments)。

## <a name="add-a-code-file"></a>新增程式碼檔案

您現在準備好可新增一些 Python 程式碼來實作基本的 Web 應用程式。

1. 在**方案總管**中，以滑鼠右鍵按一下專案，然後依序選取 [新增] > [新增項目]。在出現的對話方塊中，選取 [空白 Python 檔案]，將其命名為 `hello.py`，然後選擇 [確定]。 Visual Studio 會自動在編輯器視窗中開啟檔案。 (一般而言，[新增] > [新增項目] 命令是將不同種類的檔案新增至專案中的好方法，因為項目範本通常會提供有用的未定案程式碼。)

1. 將下列程式碼複製貼入或輸入至 `hello.py`：

    ```python
    import falcon
    api = falcon.API()

    # In Falcon, define a class for each resource; the on_get 
    # method then handles any GET requests.

    class HelloResource:
        def on_get(self, req, resp):
            resp.status = falcon.HTTP_200  # 200 is the default
            resp.body = "Hello, Python!"

    # Resources are represented by long-lived class instances
    hello = HelloResource()

    # Instruct Falcon to route / and /hello to the HelloResource
    api.add_route('/', hello)
    api.add_route('/hello', hello)

    if __name__ == "__main__":
        from wsgiref.simple_server import make_server

        # Run the web server on localhost:8080
        print("Starting web app server")
        srv = make_server('localhost', 8080, api)
        srv.serve_forever()
    ```

如需 Falcon 的詳細資訊，請參閱 [Falcon Quickstart](https://falcon.readthedocs.io/en/stable/user/quickstart.html) (Falcon 快速入門) (falcon.readthedocs.io)。

## <a name="run-the-application"></a>執行應用程式

1. 以滑鼠右鍵按一下**方案總管**中的 `hello.py`，並選取 [設定為啟動檔案]。 執行應用程式時，命令會找出在 Python 中啟動的程式碼檔案。

1. 以滑鼠右鍵按一下**方案總管**中的 "Hello Python" 並選取 [屬性]。 然後選取 [偵錯] 索引標籤，將 [連接埠號碼] 屬性設定為 `8080`。 這個步驟可確保 Visual Studio 以 `localhost:8080` 啟動瀏覽器，而不是使用隨機的連接埠。

1. 選取 [偵錯] > [啟動但不偵錯](Ctrl+F5) 將變更儲存至檔案並執行應用程式。

1. 命令視窗隨即出現並顯示訊息「正在啟動 Web 應用程式伺服器」，然後瀏覽器視窗會在 `localhost:8080` 開啟，您會看到訊息 "Hello, Python!" GET 要求也會出現在命令視窗中。 (如果您在命令視窗中只看到 Python 互動式殼層，或該視窗短暫顯示在畫面上，請確定您已在前文的步驟 1 中將 `hello.py` 設定為啟動檔案。)

1. 關閉命令視窗以停止應用程式。

## <a name="next-steps"></a>後續步驟

恭喜您完成本快速入門，了解到有關 Visual Studio IDE 與 Python 的一些內容。 若要繼續更完整的 Visual Studio Python 教學課程，包括使用互動式視窗、偵錯、資料視覺效果，以及使用 Git，請選取下方的按鈕。

> [!div class="nextstepaction"]
> [教學課程：Visual Studio 中的 Python 使用者入門](../python/vs-tutorial-01-01.md)。

- 了解 [Visual Studio 中的 Python Web 應用程式範本](../python/template-web.md)
- 深入了解 [Visual Studio IDE](../ide/visual-studio-ide.md)
- 了解如何使用 [Visual Studio 偵錯工具](../debugger/debugger-feature-tour.md)