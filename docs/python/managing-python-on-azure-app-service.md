---
title: "管理 Azure App Service 上的 Python | Microsoft Docs"
ms.custom: 
ms.date: 7/12/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e56b5d55-6e6b-48af-af40-5172c768cabc
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: c00adbbabf0d3b82acb17f4a269dfc693246bc69
ms.openlocfilehash: 56fccdd5e103cf29c8ea4a93ab80de7187275642
ms.contentlocale: zh-tw
ms.lasthandoff: 08/01/2017

---

# <a name="managing-python-on-azure-app-service"></a>管理 Azure App Service 上的 Python

[Azure App Service](https://azure.microsoft.com/services/app-service/) 是一種適用於 Web 應用程式的平台即服務供應項目，不論它們是否為透過瀏覽器、您自己的用戶端所使用的 REST API 或是事件觸發處理所存取的網站。 App Service 完全支援使用 Python 來實作應用程式。

Azure App Service 上的 Python 支援是以一組 App Service 網站延伸模組形式提供，而每個延伸模組都會包含特定版本的 Python 執行階段。 一定會建議使用最新的 Python 3 版本，但您可以在必要時選擇較舊的版本。 本主題說明如何安裝和設定網站延伸模組，以及任何所需的套件。

> [!Note]
> 此處所述的程序得隨時變更，特別是改善。 變更宣告於 [Python Engineering at Microsoft blog](https://blogs.msdn.microsoft.com/pythonengineering/) (Microsoft 部落格的 Python 工程)。

## <a name="choosing-a-python-version-through-the-azure-portal"></a>透過 Azure 入口網站選擇 Python 版本

如果已經在 Azure App Service 上部署和執行您的網站，請巡覽至 [App Service] 刀鋒視窗，並捲動至 [開發工具] 區段，然後選取 [延伸模組] > [新增]。 捲動清單，找到您想要 Python 版本的特定延伸模組 (但清單無法進行排序，因此，不同的版本會分散到清單各處)：

![顯示 Python 延伸模組的 Azure 入口網站](media/python-on-azure-extensions.png)

## <a name="choosing-a-python-version-through-the-azure-resource-manager"></a>透過 Azure Resource Manager 選擇 Python 版本

如果您要使用 Azure Resource Manager 範本來部署網站，請將網站延伸模組新增為資源。 延伸模組會顯示為類型 `siteextensions` 且名稱來自 [siteextensions.net](https://www.siteextensions.net/packages?q=Tags%3A%22python%22) 之網站的巢狀資源。

例如，新增 `python361x64` (Python 3.6.1 x64) 的參考之後，您的範本可能如下所示：

```json
  "resources": [
    {
      "apiVersion": "2015-08-01",
      "name": "[parameters('siteName')]",
      "type": "Microsoft.Web/sites",
      ...
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
      ...
```

## <a name="configuring-your-site"></a>設定網站

安裝網站延伸模組之後 (透過入口網站或 Azure Resource Manager 範本)，Python 安裝路徑就像 `d:\home\python361x64\python.exe`。 若要查看特定路徑，請在針對 App Service 顯示的清單中選取延伸模組，以開啟其包含路徑的描述頁面：

![Azure App Service 上的延伸模組清單](media/python-on-azure-extension-list.png)

![Azure App Service 上的延伸模組詳細資料](media/python-on-azure-extension-detail.png)

您的下一個步驟是參考 FastCGI 和 HTTP 平台要求處理常式之網站 `web.config` 檔案中的 Python 安裝。

### <a name="using-the-fastcgi-handler"></a>使用 FastCGI 處理常式

FastCGI 是一種在要求層級運作的介面。 IIS 會接收連入連線並將每個要求轉送至在一或多個持續性 Python 程序中執行的 WSGI 應用程式。 每個 Python 網站延伸模組都已預先安裝和設定 [wfastcgi 套件](https://pypi.io/project/wfastcgi)，因此您可以在 `web.config` 中包含下列程式碼輕鬆地予以啟用：

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <appSettings>
    <add key="PYTHONPATH" value="D:\home\site\wwwroot"/>
    <add key="WSGI_HANDLER" value="app.wsgi_app"/>
    <add key="WSGI_LOG" value="D:\home\LogFiles\wfastcgi.log"/>
  </appSettings>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule" scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py" resourceType="Unspecified" requireAccess="Script"/>
    </handlers>
  </system.webServer>
</configuration>
```

`<appSettings>` 可供您的應用程式作為環境變數：
- `PYTHONPATH` 的值可能可以自由地擴充，但必須包含您網站的根目錄。
- `WSGI_HANDLER` 必須指向可從您的網站匯入的 WSGI 應用程式。
- `WSGI_LOG` 是選擇性的，但建議用於偵錯您的網站。 

在 `<handlers>` 下，確定 `<add>` 項目中的 `scriptProcessor` 屬性包含特定安裝的正確路徑。 路徑會再次顯示於延伸模組的詳細資料刀鋒視窗上。

### <a name="using-the-http-platform-handler"></a>使用 HTTP 平台處理常式

HTTP 平台模組會將通訊端連線直接傳遞至獨立 Python 程序。 這個傳遞可讓您執行任何喜歡的網頁伺服器，但需要執行本機網頁伺服器的啟動指令碼。 您可以在 `<httpPlatform>` 項目中指定指令碼，其中 `processPath` 屬性指向 Python，而 `arguments` 屬性指向您的指令碼以及您想要提供的任何引數：

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

當然，組態中 `python.exe` 的路徑是您已安裝版本所特有。

程式碼中所顯示的 `HTTP_PLATFORM_PORT` 環境變數包含本機伺服器應該接聽 localhost 連線的連接埠。 此範例也會示範如何建立另一個環境變數 (如有需要)，在此情況下，是 `SERVER_PORT`。

## <a name="installing-packages"></a>安裝套件

因為您的應用程式可能與各種套件相依，所以您需要透過下列三種方法之一，確定 App Service 的 Python 環境中已安裝這些套件：

- Azure 入口網站上的 Azure App Service 主控台
- Kudu REST API
- 將每個程式庫複製至應用程式原始程式碼

### <a name="kudu-console"></a>Kudu 主控台

[Kudu console](https://github.com/projectkudu/kudu/wiki/Kudu-console) (Kudu 主控台) 可讓您透過直接且提高權限的命令列存取 App Service 伺服器和其檔案系統。 除了是重要的偵錯工具之外，它也可以用於以 CLI 為基礎的組態。

選取 [開發工具] > [進階工具] 以從 App Service 刀鋒視窗存取 Kudu，然後選取 [執行] 以巡覽至與基礎 App Service URL 相同的 URL，但會插入 `.scm`。 例如，如果您的基底 URL 是 `https://vspython-test.azurewebsites.net/`，則 Kudu 位於 `https://vspython-test.scm.azurewebsites.net/`：

![Azure App Service 的 Kudu 主控台](media/python-on-azure-console01.png)

選取 [偵錯主控台] > [CMD] 開啟主控台，您可以在其中巡覽至 Python 安裝，並查看現有的程式庫。

安裝單一套件：

1. 巡覽至您想要安裝套件的 Python 安裝資料夾，例如 `d:\home\python361x64`。
1. 使用 `python.exe -m pip install <package_name>` 來安裝套件。

![透過 Azure App Service 的 Kudu 主控台安裝 matplotlib 的範例](media/python-on-azure-console02.png)

從 `requirements.txt` 安裝套件 (建議)：

1. 巡覽至您想要安裝套件的 Python 安裝資料夾，例如 `d:\home\python361x64`。
1. 使用 `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt` 來安裝套件。

建議使用 requirements.txt，因為它可以輕鬆地重現您在本機和伺服器上設定的確切套件。

> [!Note]
> 您的網頁伺服器上沒有 C 編譯器，因此您需要安裝任何具有原生延伸模組之套件的滾輪。 許多熱門的套件都會提供自己的滾輪。 如果是未提供的套件，請在本機開發電腦上使用 `pip wheel <package_name>`，然後將滾輪上傳至您的網站。 如需範例，請參閱[管理必要套件](python-environments.md#managing-required-packages)。

### <a name="kudu-rest-api"></a>Kudu REST API

您可以將命令張貼到 `https://yoursite.scm.azurewebsites.net/api/command` 以透過 Kudu REST API 遠端執行命令，而不是透過 Azure 入口網站使用 Kudu 主控台。 例如，若要安裝 `matplotlib` 套件，請將下列 JSON 張貼到 `/api/command`：

```json
{
    "command": 'python.exe -m pip install matplotlib',
    "dir": '\home\python361x64'
}
```

如需命令和驗證的資訊，請參閱 [Kudu 文件](https://github.com/projectkudu/kudu/wiki/REST-API)。 您也可以從 Azure CLI 使用 [`az webapp deployment list-publishing-profiles command`](https://docs.microsoft.com/cli/azure/webapp/deployment#list-publishing-profiles) 來查看認證。 公佈 Kudu 命令的協助程式程式庫也[在 GitHub 上提供使用](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42) \(英文\)。


### <a name="copying-libraries-into-app-source-code"></a>將程式庫複製至應用程式原始程式碼

您可以改為將程式庫複製至您自己的原始程式碼並進行部署，就像它們是您應用程式的一部分，而不是直接在伺服器上安裝套件。 根據更新它們的相依性數目和頻率，這個方法可能是讓工作中部署進行的最簡單方式。

需要注意的是，這些程式庫必須精確地符合伺服器上的 Python 版本，否則您在部署之後會看到不容易了解的錯誤。 不過，因為 App Service 網站延伸模組中的 Python 版本與 python.org 上發行的版本完全相同，所以您可以輕鬆地取得進行本機開發的相容版本。

### <a name="avoiding-virtual-environments"></a>避免虛擬環境

雖然在虛擬環境中本機工作可協助您完全了解網站所需的相依性，但是不建議在 App Service 上使用虛擬環境。 相反地，只要將程式庫安裝到您的主要 Python 資料夾，並部署它們與您的應用程式，即可避免相依性衝突。

