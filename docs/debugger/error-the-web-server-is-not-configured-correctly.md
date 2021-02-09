---
title: 未正確設定 web 伺服器 |Microsoft Docs
ms.date: 09/20/2017
ms.topic: error-reference
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3a5c50822b516b73206791e3d8538bd174cfc8f6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871230"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>錯誤：未正確設定 Web 伺服器

當您採取詳細步驟來解決問題，並在再次嘗試進行調試之前，您可能也需要重設 IIS。 您可以開啟系統管理員命令提示字元並輸入 `iisreset` 。

請採取下列步驟來解決此問題：

1. 如果伺服器上裝載的 web 應用程式已設定為發行組建，請重新發行為 Debug 組建，然後確認 web.config 檔案包含 `debug=true` 在編譯元素中。 重設 IIS 並重試。

    例如，如果您使用發行組建的發行設定檔，請將它變更為 [Debug] 和 [重新發佈]。 否則， `false` 當您發行時，debug 屬性將會設定為。

2.  (IIS) 驗證實體路徑是否正確。 在 IIS 中，您可以在 [基本設定] 中找到這項設定 **> 實體路徑** (或較舊版本的 IIS) 中的 [ **Advanced settings** ]。

    如果 web 應用程式已複製到不同的電腦、手動重新命名或移動，實體路徑可能會不正確。 重設 IIS 並重試。

3. 如果您要在 Visual Studio 的本機進行偵錯工具，請確認已在 [屬性] 中選取正確的伺服器。 根據您的專案類型， (開啟 [ **Web > 伺服器** ] 或 [屬性] > **> Debug** 。 針對 Web Form 專案，開啟 [ **屬性頁] > [> 伺服器**) 的 [開始選項]。

    如果您使用外部 (自訂) 伺服器（例如 IIS），則 URL 必須正確。 否則，請選取 IIS Express 並重試。

4.  (IIS) 確定已在伺服器上安裝正確的 ASP.NET 版本。

    IIS 和 Visual Studio 專案中的 ASP.NET 版本不相符，可能會造成此問題。 您可能需要在 web.config 中設定 framework 版本。若要在 IIS 上安裝 ASP.NET，請使用 [Web Platform Installer (WebPI) ](https://www.microsoft.com/web/downloads/platform.aspx)。 此外，請參閱 [使用 ASP.NET 3.5 和 ASP.NET 4.5 的 IIS 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) ，或針對 ASP.NET Core， [使用 iis 在 Windows 上裝載](https://docs.asp.net/en/latest/publishing/iis.html)。

4. 如果 `maxConnection` IIS 的限制太低，而且您有太多連線，您可能需要 [增加連接限制](/iis/configuration/system.applicationhost/sites/sitedefaults/limits)。

## <a name="see-also"></a>另請參閱
- [在遠端 IIS 電腦上對 ASP.NET 進行遠端偵錯](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)