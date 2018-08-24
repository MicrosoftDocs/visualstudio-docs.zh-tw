---
title: Python 的 Azure 遠端偵錯
description: 如何設定 Azure App Service 以使用 Visual Studio 來為 Python 應用程式進行遠端偵錯。
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 1e3e70675901128ed6b8d118e54dc10ddee152a5
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40008615"
---
# <a name="remotely-debug-python-code-on-azure"></a>對 Azure 上的 Python 程式碼進行遠端偵錯

[Visual Studio 中的 Python 支援](installing-python-support-in-visual-studio.md)包括能夠對 Azure App Service 上執行的 Python 程式碼進行遠端偵錯。 不同於簡單的遠端偵錯，此案例中的目標電腦無法透過 TCP 直接存取；因此，Visual Studio 提供可透過 HTTP 公開偵錯工具通訊協定的 Proxy。 使用網站範本建立的專案會在產生的 *web.debug.config* 檔案中自動設定此 Proxy。 當您發佈您專案的 [偵錯] 組態時，也會啟用遠端偵錯，如[發佈至 Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md) 所述。

由於 Azure 遠端偵錯使用 Web 通訊端，因此必須透過 [Azure 入口網站](https://portal.azure.com) 為您的 App Service 啟用通訊端，方法是前往 [設定] > [應用程式設定]，將 [一般設定] > [Web 通訊端] 設為 [開啟]，然後選取 [儲存] 以套用變更。 (請注意，**偵錯**設定不適用於 Python 偵錯。)

![在 Azure 入口網站中啟用 Web 通訊端](media/azure-remote-debugging-enable-web-sockets.png)

## <a name="attach-with-server-explorer"></a>使用伺服器總管附加

一旦您的專案已正確部署並已啟用 Web 通訊端，即可從 Visual Studio 中的 [伺服器總管] 附加到 App Service ([檢視] > [伺服器總管])。 在 [Azure] > [App Service] 下尋找您的網站和適用的資源群組，按一下滑鼠右鍵並選取 [附加偵錯工具 (Python)] ([附加偵錯工具] 命令適用於在 IIS 下執行的 .NET 應用程式，且只有在連同 Python 應用程式一併裝載 .NET 程式碼時才有用)。

Visual Studio 可能會直接提供您一連串的指示來直接附加，如以下的[不使用伺服器總管附加](#attach-without-server-explorer)所述。 如果看不到 [附加偵錯工具 (Python)] 命令或 Visual Studio 無法附加到您的網站，請參閱[適用於 Python 和 Azure 的遠端偵錯疑難排解工具](debugging-remote-python-code-on-azure-troubleshooting.md)。

如果連接成功，Visual Studio 會切換成偵錯工具檢視。 工具列指出偵錯中的處理序，例如 `wss://` URI：

![正在對 Azure App Service 網站進行偵錯](media/azure-remote-debugging-attached.png)

一旦附加，偵錯體驗與一般遠端偵錯的體驗大致相同，但受到一些限制。 尤其是，處理連入要求並透過 FastCGI 將它們委派至 Python 程式碼的 IIS Web 伺服器有一個要求處理逾時，預設為 90 秒。 如果要求處理時間超過此逾時 (例如，因為處理序在中斷點暫停)，IIS 會終止處理序，結束您的偵錯工作階段。 

## <a name="attach-without-server-explorer"></a>不使用伺服器總管附加

若要將偵錯工具直接附加到 App Service，請依照 Visual Studio 部署至您的網站 (位於 *\<site_url>/ptvsd*，例如 *ptvsdemo.azurewebsites.net/ptvsd*) 的 WebSocket Proxy 資訊頁面上的指示進行。 瀏覽此頁面也可確認 Proxy 已正確設定：

![Azure 遠端偵錯 Proxy 資訊頁面](media/azure-remote-debugging-proxy-info-page.png)

遵循指示，使用 *web.debug.config* 中的密碼建構 URL，這個檔案在每次發佈您的專案時都會重新產生。 這個檔案在 [方案總管] 中預設為隱藏，而且未包含在專案中，因此請顯示所有檔案，或在不同的編輯器中開啟它。 一旦您開啟檔案，請查看名為 `WSGI_PTVSD_SECRET` 的 appSetting 的值：

![判斷 Azure App Service 中的偵錯工具端點](media/azure-remote-debugging-secret.png)

現在，您的 URL 格式必須是 `wss://<secret>@<site_name>.azurewebsites.net/ptvsd`，其中的 &lt;secret&gt; 與 &lt;site_name&gt; 必須以您所指定的值取代。

若要附加偵錯工具，請選取 [偵錯] > [附加至處理序]，選取 [傳輸] 下拉式清單中的 [Python 遠端偵錯]，在 [限定詞文字方塊] 中輸入該 URL，然後按 **Enter** 鍵。 如果 Visual Studio 可以成功連線至 App Service，它會在清單中顯示一個 Python 處理序。 依序選取該處理序、[附加 (Attach)] 以開始偵錯︰

![使用 [附加至處理序 (Attach to Process)] 對話方塊附加至 Azure 網站](media/azure-remote-debugging-manual-attach.png)
