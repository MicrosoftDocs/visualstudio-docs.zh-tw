---
title: 設定 Azure App Service 上的 Python (Windows)
description: 如何在 Azure App Service 上安裝 Python 解譯器和程式庫，並設定 Web 應用程式以便能正確地參考該解譯器。
ms.date: 01/07/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: b76bc008c30efdee0185e6f122abaff8457acef6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882787"
---
# <a name="how-to-set-up-a-python-environment-on-azure-app-service-windows"></a>如何在 Azure App Service 上設定 Python 環境 (Windows)

> [!Important]
> Microsoft 已經取代本文所述之適用於 Windows 上 App Service 的 Python 延伸模組，改為直接部署到 [Linux 上的 App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)。

[Azure App Service](https://azure.microsoft.com/services/app-service/) 是一種適用於 Web 應用程式的平台即服務供應項目，不論它們是否為透過瀏覽器、您自己的用戶端所使用的 REST API 或是事件觸發處理所存取的網站。 App Service 完全支援使用 Python 來實作應用程式。

Azure App Service 是以一組 App Service「網站延伸模組」的形式來支援可自訂的 Python，且每個延伸模組都包含特定版本的 Python 執行階段。 如此一來，您即可將任何所需的套件直接安裝到該環境中，如本文章所述。 您可以在 App Service 當中自訂環境，即不需要維護 Web 應用程式專案中的套件，或使用應用程式程式碼來上傳套件。

> [!Tip]
> 雖然 App Service 預設已在伺服器根資料夾中安裝 Python 2.7 和 Python 3.4，但您無法在這些環境中自訂或安裝套件，因此也不應該依賴這些套件。 反之，您應該倚賴自己所控制的網站延伸模組，如本文章所述。

## <a name="choose-a-python-version-through-the-azure-portal"></a>透過 Azure 入口網站選擇 Python 版本

1. 在 Azure 入口網站中，為您的 Web 應用程式建立 App Service。
1. 在 App Service 頁面中，捲動到 [開發工具] 區段，再依序選取 [延伸模組] 和 [+ 新增]。
1. 向下捲動至含有所需 Python 版本的延伸模組清單中：

    ![顯示 Python 延伸模組的 Azure 入口網站](media/python-on-azure-extensions.png)

    > [!Tip]
    > 如果您需要較舊的 Python 版本，但網站延伸模組並未列出這個版本，您仍然可以透過 Azure Resource Manager 進行安裝，如下一節所述。

1. 選取延伸模組，並接受法律條款，然後選取 [確定]。
1. 安裝完成時，入口網站即會顯示通知。

## <a name="choose-a-python-version-through-the-azure-resource-manager"></a>透過 Azure Resource Manager 選擇 Python 版本

如果您要使用 Azure Resource Manager 範本來部署 App Service，請將網站延伸模組新增為資源。 特別是，延伸模組會顯示為巢狀資源 (`resources` 下的 `resources` 物件) ，其類型為 `siteextensions` 並具有來自 [siteextensions.net](https://www.siteextensions.net/packages?q=Tags%3A%22python%22) 的名稱。

例如，新增 `python361x64` (Python 3.6.1 x64) 的參考之後，您的範本可能如下所示 (已省略部分屬性)：

```json
"resources": [
  {
    "apiVersion": "2015-08-01",
    "name": "[parameters('siteName')]",
    "type": "Microsoft.Web/sites",

    // ...

    "resources": [
      {
        "apiVersion": "2015-08-01",
        "name": "python361x64",
        "type": "siteextensions",
        "properties": { },
        "dependsOn": [
          "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
        ]
      },
      // ...
    ]
  }
```

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>將 web.config 設定為指向 Python 解譯器

安裝網站延伸模組之後 (透過入口網站或 Azure Resource Manager 範本)，您要將應用程式的 *web.config* 檔案指向 Python 解譯器。 *web.config* 檔案會指示在 App Service 上執行的 IIS (7+) 網頁伺服器應如何透過 HttpPlatform (建議使用) 或 FastCGI 來處理 Python 要求。

請先從尋找網站延伸模組的 *python.exe* 完整路徑開始，然後建立並修改適當的 *web.config* 檔案。

### <a name="find-the-path-to-pythonexe"></a>尋找 python.exe 的路徑

Python 網站延伸模組會安裝在伺服器的 *d:\home* 下方，適當的 Python 版本和架構資料夾中 (少數較舊版本例外)。 例如，Python 3.6.1 x64 會安裝在 *d:\home\python361x64* 中。 因此，Python 解譯器的完整路徑即為 *d:\home\python361x64\python.exe*。

若要查看 App Service 上的特定路徑，請選取 App Service 頁面的 [延伸模組]，然後選取清單中的延伸模組。

![Azure App Service 上的延伸模組清單](media/python-on-azure-extension-list.png)

這個動作會開啟延伸模組描述頁面，其中包含路徑：

![Azure App Service 上的延伸模組詳細資料](media/python-on-azure-extension-detail.png)

如果您無法查看延伸模組的路徑，可以手動使用主控台來尋找：

1. 在 [App Service] 頁面上，選取 [**開發工具**]  >  **主控台**。
1. 輸入 `ls ../home` 或 `dir ..\home` 命令，以查看最上層的延伸模組資料夾，例如 *Python361x64*。
1. 輸入 `ls ../home/python361x64` 或 `dir ..\home\python361x64` 之類的命令，以驗證該資料夾中包含 *python.exe* 和其他解譯器檔案。

### <a name="configure-the-httpplatform-handler"></a>設定 HTTP 平台處理常式

HTTP 平台處理常式模組會將通訊端連線直接傳遞給獨立的 Python 處理序。 這個傳遞可讓您執行任何喜歡的網頁伺服器，但需要執行本機網頁伺服器的啟動指令碼。 您可以在 *web.config* 的 `<httpPlatform>` 元素中指定指令碼，其中 `processPath` 屬性指向網站延伸模組的 Python 解譯器，而 `arguments` 屬性則指向您的指令碼以及您想要提供的任何引數：

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="D:\home\Python361x64\python.exe"
                  arguments="D:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="D:\home\LogFiles\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SERVER_PORT" value="%HTTP_PLATFORM_PORT%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

此處所顯示的 `HTTP_PLATFORM_PORT` 環境變數包含本機伺服器應該接聽 localhost 連線的連接埠。 此範例也會示範如何建立另一個環境變數 (如有需要)，在此情況下，是 `SERVER_PORT`。

### <a name="configure-the-fastcgi-handler"></a>設定 FastCGI 處理常式

FastCGI 是一種在要求層級運作的介面。 IIS 會接收連入連線並將每個要求轉送至在一或多個持續性 Python 程序中執行的 WSGI 應用程式。 每個 Python 網站延伸模組都已預先安裝和設定 [wfastcgi 套件](https://pypi.io/project/wfastcgi)，因此，針對 Bottle 架構的 Web 應用程式，您可以在 *web.config* 中包含下列程式碼輕鬆予以啟用。 請注意，已在 `PythonHandler` 機碼中取代 *python.exe* 與 *wfastcgi.py* 的完整路徑：

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <appSettings>
    <add key="PYTHONPATH" value="D:\home\site\wwwroot"/>
    <!-- The handler here is specific to Bottle; other frameworks vary. -->
    <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
    <add key="WSGI_LOG" value="D:\home\LogFiles\wfastcgi.log"/>
  </appSettings>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
           scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
           resourceType="Unspecified" requireAccess="Script"/>
    </handlers>
  </system.webServer>
</configuration>
```

此處定義的 `<appSettings>` 可供應用程式作為環境變數：

- `PYTHONPATH` 的值可以自由擴充，但必須包含應用程式的根目錄。
- `WSGI_HANDLER` 必須指向可從應用程式匯入的 WSGI 應用程式。
- `WSGI_LOG` 是選擇性的，但建議用於偵錯應用程式。

如需 Bottle、Flask 與 Django Web 應用程式的 *web.config* 內容詳細資料，請參閱 [發行至 Azure](publishing-python-web-applications-to-azure-from-visual-studio.md)。

## <a name="install-packages"></a>安裝套件

透過網站延伸模組安裝的 Python 解譯器只是 Python 環境的一小部分。 您可能還需要在該環境中安裝不同的套件。

若要直接在伺服器環境中安裝套件，請使用下列方法之一：

| 方法 | 使用方式 |
| --- | --- |
| [Azure App Service 的 Kudu 主控台](#azure-app-service-kudu-console) | 可透過互動方式安裝套件。 套件必須是純 Python 套件，或必須發行 Wheel。 |
| [Kudu REST API](#kudu-rest-api) | 可用來自動化安裝套件。  套件必須是純 Python 套件，或必須發行 Wheel。 |
| 應用程式套件組合 | 直接將套件安裝到您的專案中，然後將其部署到 App Service，如同套件就是應用程式的一部分。 根據更新它們的相依性數目和頻率，這個方法可能是讓工作中部署進行的最簡單方式。 請務必注意，這些程式庫必須符合伺服器上的 Python 版本，否則您在部署之後會看到奇怪的錯誤。 儘管如此，由於 App Service 網站延伸模組中的 Python 版本與 python.org 上發行的版本完全相同，因此您可以輕鬆取得適用於本機開發的相容版本。 |
| 虛擬環境 | 不支援。 請改為使用套件組合，並設定 `PYTHONPATH` 環境變數以指向套件的位置。 |

### <a name="azure-app-service-kudu-console"></a>Azure App Service 的 Kudu 主控台

[Kudu console](https://github.com/projectkudu/kudu/wiki/Kudu-console) (Kudu 主控台) 可讓您透過直接且提高權限的命令列存取 App Service 伺服器和其檔案系統。 這既是一項重要的偵錯工具，也可讓 CLI 作業 (例如安裝套件) 順利進行。

1. 選取 [**開發工具**] 的 [  >  **Advanced tools**]，然後選取 [**移至**]，從 Azure 入口網站的 App Service 頁面開啟 Kudu。 這個動作會瀏覽至與基底 App Service URL 相同的 URL，差別只在於插入了 `.scm`。 例如，如果您的基底 URL 是 `https://vspython-test.azurewebsites.net/`，則 Kudu 位於 `https://vspython-test.scm.azurewebsites.net/` (您可將其設為書籤)：

    ![Azure App Service 的 Kudu 主控台](media/python-on-azure-console01.png)

1. 選取 [ **Debug console**  >  **CMD** ] 以開啟主控台，您可以在其中流覽至 Python 安裝，並查看已有哪些程式庫。

1. 安裝單一套件：

    a. 瀏覽至您想要安裝套件的 Python 安裝資料夾，例如 *d:\home\python361x64*。

    b. 使用 `python.exe -m pip install <package_name>` 來安裝套件。

    ![透過 Azure App Service 的 Kudu 主控台安裝 Bottle 的範例](media/python-on-azure-console02.png)

1. 如果您已將應用程式的 *requirements.txt* 部署至伺服器，請安裝下列所有需求，如下所示：

    a. 瀏覽至您想要安裝套件的 Python 安裝資料夾，例如 *d:\home\python361x64*。

    b. 執行命令 `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt`。

    建議使用 *requirements.txt*，因為它可以輕鬆地重現您在本機和伺服器上設定的確切套件。 將任何變更部署至 *requirements.txt* 之後，請務必前往主控台，然後再次執行命令。

> [!Note]
> 您的 App Service 上沒有 C 編譯器，因此您需要針對任何含原生延伸模組的套件安裝 Wheel。 許多熱門的套件都會提供自己的滾輪。 如果是未提供的套件，請在本機開發電腦上使用 `pip wheel <package_name>`，然後將滾輪上傳至您的網站。 如需範例，請參閱[使用 requirements.txt 管理必要套件](managing-required-packages-with-requirements-txt.md)。

### <a name="kudu-rest-api"></a>Kudu REST API

您可以將命令張貼到 `https://yoursite.scm.azurewebsites.net/api/command` 以透過 Kudu REST API 遠端執行命令，而不是透過 Azure 入口網站使用 Kudu 主控台。 例如，若要安裝 `bottle` 套件，請將下列 JSON 張貼到 `/api/command`：

```json
{
    "command": 'python.exe -m pip install bottle',
    "dir": '\home\python361x64'
}
```

如需命令和驗證的資訊，請參閱 [Kudu 文件](https://github.com/projectkudu/kudu/wiki/REST-API)。

您也可以透過 Azure CLI 使用 `az webapp deployment list-publishing-profiles` 命令 (請參閱 [az webapp deployment](/cli/azure/webapp/deployment?view=azure-cli-latest&preserve-view=true#az-webapp-deployment-list-publishing-profiles) (az webapp 部署)) 以查看認證。 [GitHub](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42) 上也提供用於發佈 Kudu 命令的協助程式庫。
