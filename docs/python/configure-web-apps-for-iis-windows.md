---
title: 為 IIS 設定 Python Web 應用程式
description: 如何設定 Python Web 應用程式以搭配 Windows 虛擬機器的 Internet Information Services 執行。
ms.date: 12/06/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 40411f47e7deda48b04ac4efb9bb9bc18688989a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839106"
---
# <a name="configure-python-web-apps-for-iis"></a>為 IIS 設定 Python Web 應用程式

在 Windows 電腦 (包括 [Azure 上的 Windows 虛擬機器](/azure/architecture/reference-architectures/n-tier/windows-vm)) 上使用 Internet Information Services (IIS) 作為網頁伺服器時，Python 應用程式必須在其 *web.config* 檔案中包含特定設定，IIS 才能正確地處理 Python 程式碼。 電腦本身也必須安裝 Python，以及 Web 應用程式需要的所有套件。

> [!Note]
> 此文章之前曾包含在 Windows 上的 Azure App Service 上設定 Python 的指導方針。 但是在該案例中使用的 Python 延伸模組和 Windows 主機，已被 Linux 上的 Azure App Service 取代。 如需詳細資訊，請參閱[發行 Python 應用程式至 Azure App Service (Linux)](publishing-python-web-applications-to-azure-from-visual-studio.md)。 不過您還是可以在[使用 Python 延伸模組管理 Windows 上的 App Service](managing-python-on-azure-app-service.md)找到之前的文章。

## <a name="install-python-on-windows"></a>在 Windows 上安裝 Python

若要執行 Web 應用程式，請先依照[安裝 Python 解譯器](installing-python-interpreters.md)所述，直接在 Windows 主機電腦上安裝您所需的 Python 版本。

記錄 `python.exe` 解譯器的位置供後續步驟使用。 為了方便起見，您可以將該位置新增到您的 PATH 環境變數。

## <a name="install-packages"></a>安裝套件

使用專用主機時，您可以使用全域 Python 環境而不是虛擬環境來執行您的應用程式。 因此，您可以在命令提示字元執行 `pip install -r requirements.txt`，將應用程式的所有需求安裝到全域環境。

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>將 web.config 設定為指向 Python 解譯器

您應用程式的 *web.config* 檔案會指示在 Windows 上執行的 IIS (7+) 網頁伺服器應如何透過 HttpPlatform (建議使用) 或 FastCGI 來處理 Python 要求。 Visual Studio 2015 和更早版本會自動進行這些修改。 使用 Visual Studio 2017 和更新版本時，您必須手動修改 *web.config*。

### <a name="configure-the-httpplatform-handler"></a>設定 HTTP 平台處理常式

HTTP 平台處理常式模組會將通訊端連線直接傳遞給獨立的 Python 處理序。 這個傳遞可讓您執行任何喜歡的網頁伺服器，但需要執行本機網頁伺服器的啟動指令碼。 您可以在 *web.config* 的 `<httpPlatform>` 元素中指定指令碼，其中 `processPath` 屬性指向網站延伸模組的 Python 解譯器，而 `arguments` 屬性則指向您的指令碼以及您想要提供的任何引數：

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="c:\python36-32\python.exe"
                  arguments="c:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="c:\home\LogFiles\python.log"
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

FastCGI 是一種在要求層級運作的介面。 IIS 會接收連入連線並將每個要求轉送至在一或多個持續性 Python 程序中執行的 WSGI 應用程式。

若要使用它，請先依照 [pypi.org/project/wfastcgi/](https://pypi.io/project/wfastcgi) 所述安裝並設定 wfastcgi 套件。

接下來，修改應用程式的 *web.config* 檔案放入 *python.exe* 的完整路徑，並在 `PythonHandler` 機碼中放入 *wfastcgi.py*。 下列步驟假設已在 *c:\python36-32* 安裝 Python，而且您的應用程式程式碼位於 *c:\home\site\wwwroot* 中，請相應調整您的路徑：

1. 修改 *web.config* 中的 `PythonHandler` 項目，使路徑符合 Python 安裝位置 (如需詳細資料，請參閱 [IIS 設定參考](https://www.iis.net/configreference) \(英文\) (iis.net))。

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="c:\python36-32\python.exe|c:\python36-32\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. 在 `<appSettings>` *web.config* 的區段內，新增的索引鍵 `WSGI_HANDLER` 、 `WSGI_LOG` (選擇性的) 以及 `PYTHONPATH` ：

    ```xml
    <appSettings>
      <add key="PYTHONPATH" value="c:\home\site\wwwroot"/>
      <!-- The handler here is specific to Bottle; see the next section. -->
      <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
      <add key="WSGI_LOG" value="c:\home\LogFiles\wfastcgi.log"/>
    </appSettings>
    ```

    這些 `<appSettings>` 值是以環境變數形式提供給您的應用程式：

    - `PYTHONPATH` 的值可以自由擴充，但必須包含應用程式的根目錄。
    - `WSGI_HANDLER` 必須指向可從應用程式匯入的 WSGI 應用程式。
    - `WSGI_LOG` 是選擇性的，但建議用於偵錯應用程式。

1. 依據您使用的架構，妥善設定 *web.config* 中的 `WSGI_HANDLER` 項目：

    - **Bottle**：務必在 `app.wsgi_app` 後面加上括弧，如下所示。 這是必要的步驟，因為該物件是函式 (請參閱 *app.py*) 而不是變數：

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask**：將 `WSGI_HANDLER` 值變更為 `<project_name>.app`，其中 `<project_name>` 應符合您的專案名稱。 您可以查看 *runserver.py* 中的 `from <project_name> import app` 陳述式，以找出確切的識別項。 比方說，如果專案的名稱為 "FlaskAzurePublishExample"，項目會顯示如下：

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="flask_iis_example.app"/>
        ```

    - **Django**：Django 專案需要對 *web.config* 進行兩個變更。 第一，將 `WSGI_HANDLER` 值變更為 `django.core.wsgi.get_wsgi_application()` (此物件位於 *wsgi.py* 檔案中)：

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        第二，將下列項目新增至 `WSGI_HANDLER` 底下的項目，並將 `DjangoAzurePublishExample` 取代為您的專案名稱：

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="django_iis_example.settings" />
        ```

1. **僅 Django 應用程式**：在 Django 專案的 *settings.py* 檔案中，將您的網站 URL 網域或 IP 位址新增至 `ALLOWED_HOSTS` (如下所示)，並使用您的 URL 或 IP 位址取代 '1.2.3.4'：

    ```python
    # Change the URL or IP address to your specific site
    ALLOWED_HOSTS = ['1.2.3.4']
    ```

    若無法將 URL 新增至陣列，會導致錯誤 **DisallowedHost 為/無效 HTTP_HOST 標頭： ' \<site URL\> '。您可能需要將 ' \<site URL\> ' 新增至 ALLOWED_HOSTS。**

    請注意，當陣列為空時，Django 會自動允許 'localhost' 和 '127.0.0.1'，但新增您的生產環境 URL 將會移除這些功能。 基於此原因，您可能會想要個別維護 *settings.py* 的開發和生產版本，或使用環境變數來控制執行階段值。

## <a name="deploy-to-iis-or-a-windows-vm"></a>部署至 IIS 或 Windows VM

如果在專案中使用正確的 *web.config* 檔案，您就可以在 [方案總管]中，使用專案操作功能表上的 [發佈] 命令，然後選取選項 **IIS、FTP 等**，發佈至執行 IIS 的電腦。 在此案例中，Visual Studio 只會將專案檔案複製到伺服器，您要負責所有伺服器端設定。
