---
title: 快速入門：使用 Visual Studio 建立 Python web 應用程式
titleSuffix: ''
description: 在此快速入門中，您將使用 Visual Studio 和 Flask 架構來建立一個簡易的 Python Web 應用程式。
ms.date: 03/07/2019
ms.technology: vs-python
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: dc47bdb2913e2d18998663967d4da3c0a7dcdd9f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939938"
---
# <a name="quickstart-create-your-first-python-web-app-using-visual-studio"></a>快速入門：使用 Visual Studio 建立您的第一個 Python Web 應用程式

在這個 5-10 分鐘將 Visual Studio 當成 Python IDE 的簡介中，您會根據 Flask 架構 建立簡單的 Python Web 應用程式。 您會透過離散步驟建立可協助您了解 Visual Studio 基本功能的專案。

::: moniker range="vs-2017"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。 在安裝程式中，請務必選取 [Python 開發] 工作負載。

::: moniker-end

::: moniker range=">=vs-2019"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads)頁面免費進行安裝。 在安裝程式中，請務必選取 [Python 開發] 工作負載。

::: moniker-end

## <a name="create-the-project"></a>建立專案

下列步驟會建立空一個空白專案，當作應用程式的容器：

::: moniker range="vs-2017"
1. 開啟 Visual Studio 2017。

2. 從頂端功能表列中，選擇 [檔案 **> 新增 > 專案**]。

3. 在 [新增專案] 對話方塊右上角的搜尋欄位中輸入 "Python Web Project"，選擇中間清單中的 [Web 專案]，提供像是 "HelloPython" 的專案名稱，然後選擇 [確定]。

    ![已選取 Python Web專案的 [新增專案] 對話方塊](media/quickstart-python-00-web-project.png)

    如果您不使用 Python 專案範本，請執行 **Visual Studio 安裝程式**，選取 [更多]**[修改]** > ，再選取 [Python 開發] 工作負載，然後選取 [修改]。

    ![Visual Studio 安裝程式中的 Python 開發工作負載](../python/media/installation-python-workload.png)

4. 隨即在 **方案總管** 右窗格中開啟新專案。 因為專案此時未包含任何其他檔案，所以是空的。

    ![顯示新建立之空專案的方案總管](media/quickstart-python-01-empty-project.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. 開啟 Visual Studio 2019。
2. 在開始畫面選取 [建立新專案]。
3. 在 [建立新專案] 對話方塊的頂部搜尋欄位輸入 "Python web"，選擇中間清單內的 [Web 專案]，然後選取 [下一步]：

    ![以選取的 Python Web 專案建立新專案畫面](media/quickstart-python-00-web-project-2019a.png)

    如果您不使用 Python 專案範本，請執行 **Visual Studio 安裝程式**，選取 [更多]**[修改]** > ，再選取 [Python 開發] 工作負載，然後選取 [修改]。

    ![Visual Studio 安裝程式中的 Python 開發工作負載](../python/media/installation-python-workload.png)

4. 在隨後出現的 [設定新專案] 對話方塊中，輸入 "HelloPython" 作為 **專案名稱**，並指定位置，然後選取 [建立]。 (系統會自動設定 **解決方案名稱** 以符合 **專案名稱**。)

    ![設定新專案對話方塊](media/quickstart-python-00-web-project-2019b.png)

5. 隨即在 **方案總管** 右窗格中開啟新專案。 因為專案此時未包含任何其他檔案，所以是空的。

    ![顯示新建立之空專案的方案總管](media/quickstart-python-01-empty-project-2019.png)
::: moniker-end

**問題：在 Visual Studio 中為 Python 應用程式建立專案的優點為何？**

**解答**：Python 應用程式通常只使用資料夾與檔案來定義，但隨著應用程式變得越來越大，此簡單結構會變得相當麻煩，且可能牽涉到自動產生的檔案、Web 應用程式的 JavaScript 等。 Visual Studio 專案有利於管理此複雜部分。 專案 (*.pyproj* 檔案) 會識別與您專案建立關聯的所有來源和內容檔案、包含每個檔案的組建資訊、維護要與來源控制系統整合的資訊，以及協助您將應用程式整理成邏輯元件。

**問題： 什麼是顯示在 [方案總管] 中的「解決方案」？**

**解答**：Visual Studio「解決方案」是容器，可協助您以群組的方式管理一或多個相關專案，以及儲存非專案特定的組態設定。 解決方案中的專案也可以彼此參考，這樣執行某一專案 (Python 應用程式) 會自動建立第二個專案 (例如 Python 應用程式中使用的 C++ 延伸模組)。

## <a name="install-the-flask-library"></a>安裝 Flask 程式庫

Python 中的 Web 應用程式幾乎一律使用許多可用的 Python 程式庫之一來處理低階的詳細資料，例如路由 Web 要求和成形回應。 基於此目的，Visual Studio 為 Web 應用程式提供各式各樣的範本，您稍後會在此快速入門中使用其中一個。

在這裡，您會使用下列步驟將 Flask 程式庫安裝在 Visual Studio 用於此專案的預設「全域環境」。

::: moniker range="vs-2017"
1. 請展開專案的 [Python 環境] 節點，以查看專案的預設環境。

    ![顯示預設環境的方案總管](media/quickstart-python-02-default-environment.png)

2. 以滑鼠右鍵按一下環境，然後選取 [ **安裝 Python 套件**]。 此命令會開啟 [套件] 索引標籤上的 [Python 環境] 視窗。

3. 在 [搜尋] 欄位中輸入 "flask"，並選取 [pip install flask from PyPI] \(從 PyPI 進行 pip 安裝 flask\)。 接受所有的系統管理員權限提示，並觀察 Visual Studio [輸出] 視窗的進度。 (當全域環境的 packages 資料夾位於受保護的區域內，例如 *C:\Program Files*，就會提示提高權限)。

    ![使用 pip install 安裝 Flask 程式庫](media/quickstart-python-03-install-package.png)
::: moniker-end
::: moniker range=">=vs-2019"
1. 請展開專案的 [Python 環境] 節點，以查看專案的預設環境。

    ![顯示預設環境的方案總管](media/quickstart-python-02-default-environment-2019.png)

2. 以滑鼠右鍵按一下環境，然後選取 [**管理 Python 套件 ...**]。此命令會在 [**套件 (PyPI])** 索引標籤上開啟 [ **Python 環境**] 視窗。

3. 在搜尋欄位中輸入 "flask"。 如果下方搜尋方塊出現 **Flask**，您即可跳過此步驟。 否則請選取 [執行命令：pip install flask]。 接受所有的系統管理員權限提示，並觀察 Visual Studio [輸出] 視窗的進度。 (當全域環境的 packages 資料夾位於受保護的區域內，例如 *C:\Program Files*，就會提示提高權限)。

    ![使用 pip install 安裝 Flask 程式庫](media/quickstart-python-03-install-package-2019.png)
::: moniker-end

4. 安裝之後，程式庫會出現在 **方案總管** 的環境中，這表示您可以在 Python 程式碼中使用它。

    ::: moniker range="vs-2017"
    ![已安裝 Flask 程式庫，並顯示在 [方案總管] 中](media/quickstart-python-04-package-installed.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![已安裝 Flask 程式庫，並顯示在 [方案總管] 中](media/quickstart-python-04-package-installed-2019.png)
    ::: moniker-end

> [!Note]
> 開發人員不是將程式庫安裝在全域環境中，他們一般會建立「虛擬環境」並在這裡安裝特定專案的程式庫。 Visual Studio 範本一般都會提供此選項，如[快速入門 - 使用範本建立 Python 專案](../python/quickstart-02-python-in-visual-studio-project-from-template.md)中所述。

**問題：哪裡可以深入了解其他可用的 Python 套件？**

**解答**：瀏覽 [Python 套件索引](https://pypi.org/) \(英文\)。

## <a name="add-a-code-file"></a>新增程式碼檔案

您現在準備好可新增一些 Python 程式碼來實作基本的 Web 應用程式。

1. 以滑鼠右鍵按一下 **方案總管** 中的專案，然後選取 [ **加入 > 新專案**]。

1. 在出現的對話方塊中，選取 [空白 Python 檔案]，將其命名為 *app.py*，然後選取 [加入]。 Visual Studio 會自動在編輯器視窗中開啟檔案。

1. 將下列程式碼複製並貼入 *app.py*：

    ```python
    from flask import Flask

    # Create an instance of the Flask class that is the WSGI application.
    # The first argument is the name of the application module or package,
    # typically __name__ when using a single module.
    app = Flask(__name__)

    # Flask route decorators map / and /hello to the hello function.
    # To add other resources, create functions that generate the page contents
    # and add decorators to define the appropriate resource locators for them.

    @app.route('/')
    @app.route('/hello')
    def hello():
        # Render the page
        return "Hello Python!"

    if __name__ == '__main__':
        # Run the app server on localhost:4449
        app.run('localhost', 4449)
    ```

1. 您可能已經注意到 [ **加入 > 新專案** ] 對話方塊會顯示您可以新增至 python 專案的許多其他類型的檔案，包括 python 類別、python 套件、python 單元測試、 *web.config* 檔案等等。 一般而言，這些項目範本 顧名思義是使用實用的未定案程式碼建立檔案的好方法。

**問題：哪裡可以深入了解 Flask？**

**解答**：請參閱 Flask 文件，從 [Flask 快速入門](https://flask.palletsprojects.com/en/1.1.x/quickstart/#quickstart) \(英文\) 開始。

## <a name="run-the-application"></a>執行應用程式

1. 以滑鼠右鍵按一下 [方案總管] 中的 *app.py* ，然後選取 [設定為啟動檔案]。 執行應用程式時，此命令會找出在 Python 中啟動的程式碼檔案。

    ::: moniker range="vs-2017"
    ![在方案總管中設定專案的啟動檔](media/quickstart-python-05-set-as-startup-file.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![在方案總管中設定專案的啟動檔](media/quickstart-python-05-set-as-startup-file-2019.png)
    ::: moniker-end

2. 以滑鼠右鍵按一下 **方案總管** 中的專案，然後選取 [ **屬性**]。 然後選取 [偵錯] 索引標籤，將 [連接埠號碼] 屬性設定為 `4449`。 這個步驟可確保 Visual Studio 以 `localhost:4449` 啟動瀏覽器，以符合程式碼中的 `app.run` 引數。

3. 選取 [ **Debug > 啟動但不) 調試** 程式] (**Ctrl** + **F5** ，它會將變更儲存至檔案並執行應用程式。

4. 命令視窗隨即出現，並以 **HTTPs： \/ /localhost：4449執行** 訊息，而瀏覽器視窗應該會開啟至 `localhost:4449` 您看到訊息 "Hello，Python！" 的位置。 GET 要求也會出現在命令視窗中，狀態為 200。

    如果瀏覽器未自動開啟，請啟動您選擇的瀏覽器並瀏覽到 `localhost:4449`。

    如果您在命令視窗中只看到 Python 互動式殼層，或該視窗短暫顯示在畫面上，請確定您已在前文的步驟 1 中將 *app.py* 設定為啟動檔案。

5. 瀏覽到 `localhost:4449/hello` 以測試 `/hello` 資源的裝飾項目也適用。 GET 要求再次出現在命令視窗中，狀態為 200。 您可視需要自行嘗試一些其他 URL，查看它們在命令視窗中顯示 404 狀態碼。

6. 關閉命令視窗以停止應用程式，然後關閉瀏覽器視窗。

**問題：啟動但不偵錯命令和開始偵錯之間有何差異？**

**解答**：您使用 [開始偵錯] 在 [Visual Studio 偵錯工具](../python/debugging-python-in-visual-studio.md)的環境中執行應用程式，可讓您設定中斷點、檢查變數，以及一行一行地逐步執行程式碼。 在偵錯工具中，應用程式可能會執行得較慢，原因是有各種不同的攔截程序在進行偵錯。 相反地，[開始偵錯] 會直接執行應用程式，就像是您從命令列執行它一樣，沒有任何偵錯內容，而且也會自動啟動瀏覽器並瀏覽到專案屬性的 [偵錯] 索引標籤中指定的 URL。

## <a name="next-steps"></a>下一步

恭喜您從 Visual Studio 執行第一個 Python 應用程式，您已了解將 Visual Studio 當成 Python IDE 使用的一些內容！

> [!div class="nextstepaction"]
> [將應用程式部署至 Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)

因為您在本快速入門遵循的步驟都相當一般，您可能已經猜到可以且應該將它們自動化。 這類自動化就由 Visual Studio 專案範本負責。 如需建立類似於您在本文中所建立 Web 應用程式但使用較少步驟的示範，請檢閱[快速入門 - 使用範本建立 Python 專案](../python/quickstart-02-python-in-visual-studio-project-from-template.md)。

若要繼續更完整的 Visual Studio Python 教學課程，包括使用互動式視窗、偵錯、資料視覺效果，以及使用 Git，請檢閱[教學課程：Visual Studio 中的 Python 使用者入門](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md)。

若要深入探索 Visual Studio 所提供的各項功能，請選取下列連結。

- 了解 [Visual Studio 中的 Python Web 應用程式範本](../python/python-web-application-project-templates.md)。
- 深入了解 [Python 偵錯](../python/debugging-python-in-visual-studio.md)
- 深入了解一般的 [Visual Studio IDE](../get-started/visual-studio-ide.md)。
