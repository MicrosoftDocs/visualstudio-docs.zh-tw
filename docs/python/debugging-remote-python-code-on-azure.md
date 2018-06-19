---
title: Python 的 Azure 遠端偵錯
description: 如何設定 Azure App Service 以使用 Visual Studio 來為 Python 應用程式進行遠端偵錯。
ms.date: 07/12/2017
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 11a624ec6582e5e07e51de6d4ab29b84dc53d4a1
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
ms.locfileid: "32031887"
---
# <a name="remotely-debugging-python-code-on-azure"></a>對 Azure 上的 Python 程式碼進行遠端偵錯

[Visual Studio 中的 Python 支援](installing-python-support-in-visual-studio.md)包括能夠對 Azure App Service 上執行的 Python 程式碼進行遠端偵錯。 不同於簡單的遠端偵錯，此案例中的目標電腦無法透過 TCP 直接存取；因此，Visual Studio 提供可透過 HTTP 公開偵錯工具通訊協定的 Proxy。 使用網站範本建立的專案會在產生的 `web.debug.config` 檔案中自動設定此 Proxy。 遠端偵錯也會在您發佈專案的偵錯設定時啟用，如[發佈至 Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md 所述。

由於 Azure 遠端偵錯使用 Web 通訊端，因此必須透過 [Azure 入口網站](https://portal.azure.com) 為您的 App Service 啟用通訊端，方法是前往 [設定 (Settings)] > [應用程式設定 (Application settings)]，將 [一般設定 (General settings)] > [Web 通訊端 (Web sockets)] 設為 [開啟 (On)]，然後選取 [儲存 (Save)] 以套用變更。 (請注意，**偵錯**設定不適用於 Python 偵錯。)

![在 Azure 入口網站中啟用 Web 通訊端](media/azure-remote-debugging-enable-web-sockets.png)

一旦您的專案已正確部署並已啟用 Web 通訊端，即可從 Visual Studio 中的 [伺服器總管 (Server Explorer)] 附加到 App Service ([檢視 (View)] > [伺服器總管 (Server Explorer)])。 在 [Azure] > [App Service] 下尋找您的網站和適用的資源群組，以滑鼠右鍵按一下並選取 [附加偵錯工具 (Python) (Attach Debugger (Python))]。 ([附加偵錯工具]  命令適用於在 IIS 下執行的 .NET 應用程式，且只有在連同 Python 應用程式一併裝載 .NET 程式碼時才有用。)

Visual Studio 可能會直接提供您一連串的指示來直接附加，如以下的[不使用伺服器總管附加](#attaching-without-server-explorer)所述。 如果看不到 [附加偵錯工具 (Python)] 命令或 Visual Studio 無法附加到您的網站，請參閱[對 Azure 遠端偵錯進行疑難排解](debugging-remote-python-code-on-azure-troubleshooting.md)。

如果連接成功，Visual Studio 會切換成偵錯工具檢視。 工具列指出偵錯中的處理序，例如 `wss://` URI：

![正在對 Azure App Service 網站進行偵錯](media/azure-remote-debugging-attached.png)

一旦附加，偵錯體驗與一般遠端偵錯的體驗大致相同，但受到一些限制。 尤其是，處理連入要求並透過 FastCGI 將它們委派至 Python 程式碼的 IIS Web 伺服器有一個要求處理逾時，預設為 90 秒。 如果要求處理時間超過此逾時 (例如，因為處理序在中斷點暫停)，IIS 會終止處理序，結束您的偵錯工作階段。 

## <a name="attaching-without-server-explorer"></a>不使用伺服器總管附加

若要將偵錯工具直接附加到 App Service，請依照 Visual Studio 部署至您的網站 (位於 `<site_url>/ptvsd`，例如 `ptvsdemo.azurewebsites.net/ptvsd`) 的 WebSocket Proxy 資訊頁面上的指示進行。 瀏覽此頁面也可確認 Proxy 已正確設定：

![Azure 遠端偵錯 Proxy 資訊頁面](media/azure-remote-debugging-proxy-info-page.png)

遵循指示，使用 `web.debug.config` 中的密碼建構 URL，這個檔案在每次發佈您的專案時都會重新產生。 這個檔案在方案總管中預設為隱藏，而且未包含在專案中，因此請顯示所有檔案，或在不同的編輯器中開啟它。 一旦您開啟檔案，請查看名為 `WSGI_PTVSD_SECRET` 的 appSetting 的值：

![判斷 Azure App Service 中的偵錯工具端點](media/azure-remote-debugging-secret.png)

您現在需要的 URL 為以下格式：`wss://<secret>@<site_name>.azurewebsites.net/ptvsd`，您要以特定的值取代字串中的 &lt;secret&gt; 和 &lt;site_name&gt;。

若要附加偵錯工具，請選取 [偵錯 (Debug)] > [附加至處理序 (Attach to Process)]，選取 [傳輸 (Transport)] 下拉式清單中的 [Python 遠端偵錯 (Python remote debugging)]，在 [限定詞文字方塊 (Qualifier textbox)] 中輸入該 URL，然後按 Enter。 如果 Visual Studio 可以成功連線至 App Service，它會在清單中顯示一個 Python 處理序。 依序選取該處理序、[附加 (Attach)] 以開始偵錯︰

![使用 [附加至處理序 (Attach to Process)] 對話方塊附加至 Azure 網站](media/azure-remote-debugging-manual-attach.png)
