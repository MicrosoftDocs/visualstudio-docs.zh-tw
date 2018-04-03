---
title: 快速入門：使用 Visual Studio 建立您的第一個 Python Web 應用程式 | Microsoft Docs
description: 在 Visual Studio 中以 Python 來建置使用 Falcon 架構之簡易 Web 應用程式的扼要簡介。
ms.custom: ''
ms.date: 03/14/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: quickstart
dev_langs:
- python
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 2b1880d95fcb4aae04d98171c8ee7df7373aaceb
ms.sourcegitcommit: 236c250bb97abdab99d00c6525d106fc0035d7d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2018
---
# <a name="quickstart-use-visual-studio-to-create-your-first-python-web-app"></a>快速入門：使用 Visual Studio 建立您的第一個 Python Web 應用程式

在這個 5-10 分鐘的 Visual Studio 整合式開發環境 (IDE) 簡介中，您要建立簡單的 Python Web 應用程式。 如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)頁面免費進行安裝。 在安裝程式中，請務必選取 [Python 開發] 工作負載。

## <a name="create-the-project"></a>建立專案

1. 開啟 Visual Studio 2017。

1. 從頂端功能表列，依序選擇 [檔案] > [新增] > [專案]。

1. 在 [新增專案] 對話方塊的左窗格中，展開 [已安裝]，然後選取 [Python]。

1. 在中間窗格中，選擇 [Web 專案]，將專案命名為如 "HelloPython"，然後選擇 [確定]。

    ![已選取 Python Web專案的 [新增專案] 對話方塊](media/quickstart-python-00-web-project.png)

    如果您看不到 Python 專案範本，請取消 [新增專案] 對話方塊，然後從頂端功能表列中選擇 [工具] > [Get Tools and Features] (取得工具與功能) 開啟 Visual Studio 安裝程式。 選擇 [Python 開發] 工作負載，然後選擇 [修改]。

    ![Visual Studio 安裝程式中的 Python 開發工作負載](../python/media/installation-python-workload.png)

1. 隨即在**方案總管**右窗格中開啟新專案。 因為專案此時未包含任何其他檔案，所以是空的。

    ![顯示新建立之空專案的方案總管](media/quickstart-python-01-empty-project.png)

**問題：在 Visual Studio 中為 Python 應用程式建立專案的優點為何？**

解答：定義 Python 應用程式時，通常僅使用資料夾和檔案，但隨著應用程式變得越來越大，此結構會變得相當複雜，且可能牽涉到自動產生的檔案、Web 應用程式的 JavaScript 等。 Visual Studio 專案有利於管理此複雜部分。 專案 (`.pyproj` 檔案) 會識別與您專案建立關聯的所有來源和內容檔案、包含每個檔案的組建資訊、維護要與來源控制系統整合的資訊，以及協助您將應用程式整理成邏輯元件。

## <a name="install-the-falcon-library"></a>安裝 Falcon 程式庫

Python 中的 Web 應用程式幾乎一律使用許多可用的 Python 程式庫之一來處理低階的詳細資料，例如路由 Web 要求和成形回應。 基於此目的，Visual Studio 為使用 Bottle、Flask 和 Django 架構的 Web 應用程式提供各式各樣的範本。

但在本快速入門中，您要使用 Falcon 程式庫，體驗安裝套件以及從頭開始建立 Web 應用程式的過程。 (Visual Studio 目前不包括 Falcon 特定範本。)為求簡便，下列步驟會將 Falcon 安裝到預設的全域環境。

1. 請展開專案的 [Python 環境] 節點，以查看專案的預設環境。

    ![顯示預設環境的方案總管](media/quickstart-python-02-default-environment.png)

1. 以滑鼠右鍵按一下環境並選取 [安裝 Python 套件...]。此命令會開啟 [套件] 索引標籤上的 [Python 環境] 視窗。在 [搜尋] 欄位中輸入 "falcon"，並選取 ["pip install falcon" from PyPI] (PyPI 的 "pip 安裝 falcon")。 接受所有的系統管理員權限提示，並觀察 Visual Studio [輸出] 視窗的進度。 (當全域環境的 packages 資料夾位於受保護的區域內，如 `c:\program files` 時，就會提示提高權限。)

    ![安裝 Falcon 程式庫](media/quickstart-python-03-install-package.png)

1. 安裝之後，程式庫會出現在**方案總管**的環境中，這表示您可以在 Python 程式碼中使用它。

    ![已安裝 Falcon 程式庫](media/quickstart-python-04-package-installed.png)

如需 Falcon 的詳細資訊，請前往 [falconframework.org](https://falconframework.org/)。

請注意，開發人員不是將程式庫安裝在全域環境中，他們一般會建立「虛擬環境」並在這裡安裝特定專案的程式庫。 Visual Studio 中有許多 Python 專案範本包含 `requirements.txt` 檔案，它會列出範本相依的程式庫。 從這些範本之一建立專案，會觸發建立程式庫安裝所在的虛擬環境。 如需詳細資訊，請參閱[使用虛擬環境](../python/selecting-a-python-environment-for-a-project.md#using-virtual-environments)。

## <a name="add-a-code-file"></a>新增程式碼檔案

您現在準備好可新增一些 Python 程式碼來實作基本的 Web 應用程式。

1. 在**方案總管**中，以滑鼠右鍵按一下專案，然後依序選取 [新增] > [新增項目]。

1. 在出現的對話方塊中，選取 [空白 Python 檔案]，將其命名為 `hello.py`，然後選擇 [新增]。 Visual Studio 會自動在編輯器視窗中開啟檔案。 (一般而言，[新增] > [新增項目] 命令是將不同種類的檔案新增至專案中的好方法，因為項目範本通常會提供有用的未定案程式碼。)

1. 將下列程式碼複製並貼入 `hello.py`：

    ```python
    import falcon

    # In Falcon, define a class for each resource and define on_* methods
    # where * is any standard HTTP methods in lowercase, such as on_get.

    class HelloResource:
        # In this application, the single HelloResource responds to only GET
        # requests, so it has only an on_get method.

        def on_get(self, req, resp):
            resp.status = falcon.HTTP_200  # 200 is the default
            resp.body = "Hello, Python!"

    # Resources are represented by long-lived class instances
    hello = HelloResource()

    # Instruct Falcon to route / and /hello to HelloResource. If you add
    # other resources, use api.add_route to define the desired
    # resource locators for them.
    api = falcon.API()
    api.add_route('/', hello)
    api.add_route('/hello', hello)

    if __name__ == "__main__":
        # Use Python's built-in WSGI reference implementation to run
        # a web server for the application.
        from wsgiref.simple_server import make_server

        # Run the web server on localhost:8080
        print("Starting web app server")
        srv = make_server('localhost', 8080, api)
        srv.serve_forever()
    ```

1. 貼上這段程式碼之後，Visual Studio 可能會在第一行的 `falcon` 下方和第 20 行的 `wsgiref.simple.server` 下方顯示波浪線。 當 Visual Studio 仍在建置這些模組的 IntelliSense 資料庫時，會出現這些指標。

如需 Falcon 的詳細資訊，請參閱 [Falcon Quickstart](https://falcon.readthedocs.io/en/stable/user/quickstart.html) (Falcon 快速入門) (falcon.readthedocs.io)。

## <a name="run-the-application"></a>執行應用程式

1. 以滑鼠右鍵按一下**方案總管**中的 `hello.py`，並選取 [設定為啟動檔案]。 執行應用程式時，命令會找出在 Python 中啟動的程式碼檔案。

    ![在方案總管中設定專案的啟動檔](media/quickstart-python-05-set-as-startup-file.png)

1. 以滑鼠右鍵按一下**方案總管**中的 "Hello Python" 並選取 [屬性]。 然後選取 [偵錯] 索引標籤，將 [連接埠號碼] 屬性設定為 `8080`。 這個步驟可確保 Visual Studio 以 `localhost:8080` 啟動瀏覽器，而不是使用隨機的連接埠。

1. 選取 [偵錯] > [啟動但不偵錯](Ctrl+F5) 將變更儲存至檔案並執行應用程式。

1. 命令視窗隨即出現並顯示訊息「正在啟動 Web 應用程式伺服器」，然後瀏覽器視窗應會在 `localhost:8080` 開啟，您會看到訊息 "Hello, Python!" GET 要求也會出現在命令視窗中。

    如果瀏覽器未自動開啟，請啟動您選擇的瀏覽器並巡覽至 `localhost:8080`。)

    如果您在命令視窗中只看到 Python 互動式殼層，或該視窗短暫顯示在畫面上，請確定您已在前文的步驟 1 中將 `hello.py` 設定為啟動檔案。

1. 關閉命令視窗以停止應用程式，然後關閉瀏覽器視窗。

## <a name="next-steps"></a>後續步驟

恭喜您完成本快速入門，了解到有關 Visual Studio IDE 與 Python 的一些內容。 若要繼續更完整的 Visual Studio Python 教學課程，包括使用互動式視窗、偵錯、資料視覺效果，以及使用 Git，請選取下方的按鈕。

> [!div class="nextstepaction"]
> [教學課程：Visual Studio 中的 Python 使用者入門](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md)。

- 了解 [Visual Studio 中的 Python Web 應用程式範本](../python/python-web-application-project-templates.md)
- 深入了解 [Python 偵錯](../python/debugging-python-in-visual-studio.md)
- 深入了解 [Visual Studio IDE](../ide/visual-studio-ide.md)
