---
title: "從 Visual Studio 將 Python 應用程式發佈至 Azure App Service | Microsoft Docs"
description: "如何從 Visual Studio 將 Python Web 應用程式直接發佈到 Azure App Service，且包含 web.config 檔案的必要內容。"
ms.custom: 
ms.date: 09/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 893cbae11a73dc468096efbb90b7129c14015eb5
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="publishing-to-azure-app-service"></a>發佈至 Azure App Service

Visual Studio 能夠將 Python Web 應用程式直接發佈到 Azure App Service。 為了發佈到 Azure App Service，您必須將必要的檔案複製到伺服器，並設定適當的 `web.config` 檔案，以指示 Web 伺服器如何啟動您的應用程式。

Visual Studio 2017 和 Visual Studio 2015 的發佈程序有所不同。 具體而言，Visual Studio 2015 會自動執行一些步驟，包括建立 `web.config`，但這項自動化會導致長期的彈性和控制受到侷限。 Visual Studio 2017 則需要更多的手動步驟，但可讓您更精確地控制 Python 環境。 此處會說明這兩種選項。

> [!Note]
> 若要了解 Visual Studio 2015 和 Visual Studio 2017 之間的變更背景，請參閱 [Publish to Azure in Visual Studio 2017](https://blogs.msdn.microsoft.com/pythonengineering/2016/12/12/publish-to-azure-in-vs-2017/) (使用 Visual Studio 2017 發佈到 Azure) 部落格文章。

## <a name="prerequisites"></a>必要條件

針對此逐步解說，您必須具備 Bottle、Flask 或 Django 架構的 Web 應用程式專案。 如果您還沒有專案，但想要嘗試發佈程序，則可以建立簡單的測試專案，如下所示：

1. 在 Visual Studio 中，選取 [檔案] > [新增] > [專案]、搜尋 "Bottle"、選取 [Bottle Web 專案]、指定專案名稱和路徑，然後按一下 [確定]。 (Python 開發工作負載中隨附 Bottle 範本；請參閱[安裝](installing-python-support-in-visual-studio.md)。)

1. 遵循提示以安裝外部套件：選取 [安裝至虛擬環境] 和您慣用的虛擬環境基底解譯器。 一般來說，這項選擇應該與 App Service 上所安裝的 Python 版本相同。

1. 按下 F5 或選取 [偵錯] > [開始偵錯]，以進行本機的專案測試。

## <a name="create-an-azure-app-service"></a>建立 Azure App Service

您需要具備目標 App Service，才能發佈至 Azure。 為此，您可以使用 Azure 訂用帳戶建立 App Service，或使用暫時網站。

如果您還沒有訂用帳戶，可以先使用[免費的完整 Azure 帳戶](https://azure.microsoft.com/free/)，其中包含適用於 Azure 服務的贈送點數。 此外，請考慮註冊 [Visual Studio Dev Essentials](https://azure.microsoft.com/pricing/member-offers/vs-dev-essentials/)，您一整年都能在每個月取得美金 $25 的點數。

> [!Tip]
> 雖然 Azure 會要求信用卡以驗證您的帳戶，但不會對信用卡收費。 您也可以將[消費限制](/azure/billing/billing-spending-limit)設為與免費信用額度相等的金額，以確保不會產生任何額外的費用。 此外，Azure 提供免費的 App Service 方案層，很適合用於下一節所述的簡單測試應用程式。

### <a name="using-a-subscription"></a>使用訂用帳戶

使用有效的 Azure 訂用帳戶，建立 App Service 與空的 Web 應用程式，如下所示：

1. 登入 [portal.azure.com](https://portal.azure.com)。
1. 選取 [+新增]，然後依序選取 [Web + 行動] 和 [Web 應用程式]。
1. 指定 Web 應用程式的名稱，將 [資源群組] 保留為 [新建]，然後選擇 **Windows** 作業系統。
1. 依序選取 [App Service 方案/位置] 和 [新建]，並指定名稱和位置。 接下來，選取 [定價層]，向下捲動並選取 [F1 免費] 方案，然後依序按 [選取]、[確定] 和 [建立]。
1. (選擇性) 建立 App Service 之後，您可以巡覽至該處，再選取 [取得發行設定檔]，並將檔案儲存到本機。

### <a name="using-a-temporary-app-service"></a>使用暫時的 App Service

在無需 Azure 訂用帳戶的情況下，按下列方式建立暫時的 App Service：

1. 開啟瀏覽器並移至 [try.azurewebsites.net](https://try.azurewebsites.net)。
1. 選取 [Web 應用程式] 作為應用程式類型，然後選取 [下一步]。
1. 選取 [空白網站]，然後選取 [建立]。
1. 以您選擇的社交登入進行登入，在經過一小段時間之後，就可以透過顯示的 URL 存取您的網站。
1. 選取 [下載發行設定檔] 並儲存 `.publishsettings` 檔案，稍後您會使用此檔案。

## <a name="configure-python-on-azure-app-service"></a>設定 Azure App Service 上的 Python

一旦您已開始執行 App Service 與空白 Web 應用程式 (不論執行於訂用帳戶或是免費網站中)，請安裝所選版本的 Python，如[管理 Azure App Service 上的 Python](managing-python-on-azure-app-service.md) 所述。 若要從 Visual Studio 2017 進行發佈，請將與網站延伸模組一起安裝的 Python 解譯器確切路徑記錄下來，如該主題所述。

如有需要，您也可以使用這些指示中的程序安裝 `bottle` 套件，因為這個套件會在此逐步解說的其他步驟期間進行安裝。

## <a name="publish-to-app-service---visual-studio-2017"></a>發佈至 App Service - Visual Studio 2017

從 Visual Studio 2017 發佈至 Azure App Service 時，僅會將您專案中的檔案複製到伺服器。 因此，您必須建立必要的檔案來設定伺服器環境。

1. 在 Visual Studio 的方案總管中，以滑鼠右鍵按一下專案，然後選取 *[新增] > [新增項目]。在出現的對話方塊中，選取 "Azure web.config (Fast CGI)" 範本並選取 [確定]。 這會在您的專案根目錄中建立 `web.config` 檔案。

1. 修改 `web.config` 中的 `PythonHandler` 項目，讓路徑與伺服器上的 Python 安裝位置相符。 例如，若是 Python 3.6.1 x64，顯示的項目應如下所示：

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. 依據您使用的架構，妥善設定 `web.config` 中的 `WSGI_HANDLER` 項目：

    - **Bottle**：在 `app.wsgi_app` 之後加上括號，如下所示。 這是必要的步驟，因為該物件是函式 (請參閱 `app.py`) 而不是變數：

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask**：將 `WSGI_HANDLER` 值變更為 `<project_name>.app`，其中 `<project_name>` 應符合您的專案名稱。 您可以查看 `runserver.py` 中的 `from <project_name> import app` 陳述式，以找出確切的識別項。 比方說，如果專案的名稱為 "FlaskAzurePublishExample"，項目會顯示如下：

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="FlaskAzurePublishExample.app"/>
        ```

    - **Django**：若是 Django 應用程式，您需要對 `web.config` 進行兩處變更。 第一，將 `WSGI_HANDLER` 值變更為 `django.core.wsgi.get_wsgi_application()` (此物件位於 `wsgi.py` 檔案中)：

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        第二，將下列項目新增至 `WSGI_HANDLER` 底下的項目，並將 `DjangoAzurePublishExample` 取代為您的專案名稱：

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="DjangoAzurePublishExample.settings" />
        ```

1. **僅限 Django 應用程式**：在符合專案名稱的資料夾中，開啟 `settings.py`，並將您的網站 URL 網域新增至 `ALLOWED_HOSTS`，如下所示，當然也要將 'vspython-test-02.azurewebsites.net' 取代為您的 URL：

    ```python
    # Change the URL to your specific site
    ALLOWED_HOSTS = ['vspython-test-02.azurewebsites.net']
    ```

    若您未將 URL 新增至陣列，會導致下列錯誤：「不允許的主機/無效的 HTTP_HOST 標頭: '\<網站 URL\>' 。 您可能需要將 '\<網站 URL\>' 新增至 ALLOWED_HOSTS。」

1. 在方案總管中，展開與您的專案同名的資料夾，再以滑鼠右鍵按一下 `static` 資料夾，選取 [新增] > [新增項目]，然後依序選取「Azure 靜態檔案 web.config」範本和 [確定]。 這個動作會在 `static` 資料夾中建立另一個 `web.config`，以停用該資料夾的 Python 處理。 此組態會將靜態檔案的要求傳送給預設的網頁伺服器，而不是使用 Python 應用程式。

1. 儲存您的專案，然後在 Visual Studio 的方案總管中，以滑鼠右鍵按一下專案，然後選取 [發行]。

1. 在顯示的 [發行] 索引標籤中，選取發行目標：

    a. 您自己的 Azure 訂用帳戶：依序選取 [Microsoft Azure App Service]、[選取現有] 以及 [發行]。 對話方塊隨即出現，您可以在其中選取適當的訂用帳戶和 App Service。 如果未顯示 App Service，請如下所述，使用下載的發行設定檔以取得暫時的 App Service。

    ![發佈至 Azure 步驟 1, Visual Studio 2017, 現有的訂用帳戶](media/tutorials-common-publish-1a-2017.png)

    b. 如果您是在 try.azurewebsites.net 上使用暫時的 App Service，或需要使用發行設定檔，請選取 **>** 控制項以尋找 [匯入設定檔]，然後依序選取該選項與 [發行]。 即會提示先前下載的 `.publishsettings` 檔案位置。

    ![發佈至 Azure 步驟 1, Visual Studio 2017, 暫時的 App Service](media/tutorials-common-publish-1b-2017.png)

1. Visual Studio 會在 [Web 發行活動] 視窗和 [發行] 視窗中顯示發行狀態。 當發行完成之後，預設瀏覽器會開啟網站 URL。 URL 也會顯示在 [發行] 視窗中。

1. 當瀏覽器開啟時，您可能會看到下列訊息：「發生內部伺服器錯誤，無法顯示此網頁。」 此訊息表示您在伺服器上的 Python 環境未完全設定，在此情況下，請執行下列步驟：

    a. 再次參閱[管理 Azure App Service 上的 Python](managing-python-on-azure-app-service.md)，確定您已安裝適當的 Python 網站延伸模組。

    b. 再次檢查 `web.config` 檔案中的 Python 解譯器路徑。 該路徑必須完全符合您所選擇的網站延伸模組安裝位置。

    c.  使用 Kudu 主控台，升級應用程式 `requirements.txt` 檔案中列出的任何套件：瀏覽至 `web.config` 中使用的相同 Python 資料夾 (例如 `/home/python361x64`)，然後按照 [Kudu 主控台](managing-python-on-azure-app-service.md#azure-app-service-kudu-console)一節所述，執行下列命令：

    ```command
    python -m pip install --upgrade -r /home/site/wwwroot/requirements.txt
    ```

    如果執行此命令時顯示權限錯誤，請再次檢查，並確認您是在網站延伸模組資料夾中執行命令，而「不是」在其中一個 App Service 的預設 Python 安裝資料夾中。 因為您無法修改預設環境，所以嘗試安裝套件必然會失敗。

    d. 如需詳細的錯誤輸出，請將下列這一行新增至 `<system.webServer>` 節點內的 `web.config`，即可提供更詳細的錯誤輸出：

    ```xml
    <httpErrors errorMode="Detailed"></httpErrors>
    ```

    e. 安裝新的套件之後，請嘗試重新啟動 App Service。 每當 `web.config` 變更時，App Service 都會自動重新啟動，因此變更 `web.config` 時，並不需要重新啟動。

    > [!Tip] 
    > 如果您針對應用程式的 `requirements.txt` 檔案進行任何變更，請務必再次使用 Kudu 主控台，安裝該檔案現在列出的任何套件。 

1. 完全設定好伺服器環境之後，請重新整理瀏覽器的網頁，即應該會顯示 Web 應用程式。

    ![將 Bottle、Flask 和 Django 應用程式發行至 App Service 的結果](media/azure-publish-results.png)

## <a name="publishing-to-app-service---visual-studio-2015"></a>發佈至 App Service - Visual Studio 2015

> [!Note] 
> 如需此程序的短片，請觀看 [Visual Studio Python Tutorial: Building a Website](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) (Visual Studio Python 教學課程：建置網站，youtube.com，3 分 10 秒)。

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，選取 [發行]。

1. 在 [發行] 對話方塊中，選取 [Microsoft Azure App Service]：

  ![發佈至 Azure 步驟 1](media/tutorials-common-publish-1.png)

1. 選取目標：

    - 如果您有 Azure 訂用帳戶，請選取 [Microsoft Azure App Service] 作為 發佈目標，然後在下列對話方塊中選取現有的 App Service，或選取 [新增] 以建立新的 App Service。
    - 如果您是使用來自 try.azurewebsites.net 的暫時網站，請選取 [匯入] 作為發佈目標，然後瀏覽至從網站下載的 `.publishsettings` 檔案，並選取 [確定]。

1. App Service 詳細資料會出現在 [發行] 對話方塊的 [連線] 索引標籤中，如下所示。

  ![發佈至 Azure 步驟 2](media/tutorials-common-publish-2.png)

1. 視需要選取 [下一步 >] 以檢閱其他設定。 如果您計畫[在 Azure 上對 Python 程式碼進行遠端偵錯](debugging-remote-python-code-on-azure.md)，您必須將 [組態] 設定為 [偵錯]

1. 選取 [發行]。 將您的應用程式部署至 Azure 之後，就會在該網站上開啟您的預設瀏覽器。 

在這個程序期間，Visual Studio 也會執行下列步驟：

- 在伺服器上建立 `web.config` 檔案，其中包含應用程式 `wsgi_app` 函式的適當指標，以及 App Service 的預設 Python 3.4 解譯器指標。
- 關閉專案的 `static` 資料夾中的檔案處理程序 (`web.config` 中有此規則)。
- 將虛擬環境發佈到伺服器。
- 新增 `web.debug.config` 檔案與 ptvsd 偵錯工具，以啟用遠端偵錯。

如前文所述，這些自動步驟可以簡化發佈程序，但卻讓您更難控制 Python 環境。 例如，系統只會在伺服器上建立 `web.config` 檔案，而不會新增至您的專案。 發佈程序也會花較長的時間進行，因為它是從您的開發電腦複製整個虛擬環境，而不是仰賴伺服器組態。

最後，您可能會想要維護自己的 `web.config` 檔案，並使用 `requirements.txt` 直接維護伺服器上的套件。 尤其是使用 `requirements.txt` 時，可以保證您的開發和伺服器環境總是相符。

## <a name="remote-debugging-on-azure-app-service"></a>Azure App Service 上的遠端偵錯

當您從 Visual Studio 2015 發佈偵錯組態時，處理程序會自動建立 `web.debug.config` 檔案，並新增包含必要偵錯工具的 `ptvsd` 資料夾。

使用 Visual Studio 2017 時，您反而需要將這些元件直接新增至專案。 以滑鼠右鍵按一下方案總管中的專案，選取 [新增] > [新增項目]，然後選取「Azure 遠端偵錯 web.config」範本。 偵錯 `web.debug.config` 檔案和 `ptvsd` 工具資料夾隨即出現在您的專案中。

將這些檔案都部署到伺服器之後 (Visual Studio 2015 會自動執行；Visual Studio 2017 則會等到下一次發行)，即可遵循 [Azure 遠端偵錯](debugging-remote-python-code-on-azure.md)的指示。
