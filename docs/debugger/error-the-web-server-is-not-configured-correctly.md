---
title: 錯誤：未正確設定 web 伺服器 |Microsoft Docs
ms.date: 09/20/2017
ms.topic: troubleshooting
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be5db0a08a287e2611c29396e96e72719b5106a7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736922"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>錯誤：未正確設定 Web 伺服器

採取這裡詳述的步驟來解決此問題，而且在嘗試再次進行 debug 之前，您可能也需要重設 IIS。 若要這麼做，請開啟系統管理員命令提示字元，然後輸入 `iisreset`。

請採取下列步驟來解決此問題：

1. 如果在伺服器上主控的 web 應用程式設定為發行組建，請重新發行為 Debug 組建，並確認 web.config 檔案中包含編譯元素中 `debug=true`。 重設 IIS 並重試。

    例如，如果您使用發行組建的發行設定檔，請將它變更為 Debug 並重新發佈。 否則，當您發行時，debug 屬性會設定為 `false`。

2. IIS請確認實體路徑是否正確。 在 IIS 中，您可以在 [**基本設定] > [實體路徑**] （或舊版 IIS 的 [ **Advanced settings** ]）中找到這項設定。

    如果 web 應用程式複製到另一部電腦、手動重新命名或移動，實體路徑可能不正確。 重設 IIS 並重試。

3. 如果您要在 Visual Studio 中本機進行偵錯工具，請確認已在 [屬性] 中選取正確的伺服器。 （開啟 [**屬性] > Web > 伺服器**或**屬性 >** 根據您的專案類型進行 Debug。 若為 Web form 專案，請開啟 **屬性頁 > 啟動選項 > 伺服器**）。

    如果您使用的是外部（自訂）伺服器（例如 IIS），URL 必須正確。 否則，請選取 IIS Express，然後再試一次。

4. IIS請確定伺服器上已安裝正確的 ASP.NET 版本。

    IIS 和 Visual Studio 專案中的 ASP.NET 版本不相符，可能會造成此問題。 您可能需要在 web.config 中設定 framework 版本。若要在 IIS 上安裝 ASP.NET，請使用[Web Platform Installer （WebPI）](https://www.microsoft.com/web/downloads/platform.aspx)。 此外，請參閱[使用 ASP.NET 3.5 和 ASP.NET 4.5 的 IIS 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) ，或針對 ASP.NET Core，使用[iis 在 Windows 上裝載](https://docs.asp.net/en/latest/publishing/iis.html)。

4. 如果 IIS 中的 `maxConnection` 限制太低，而您有太多連線，您可能需要[增加連接限制](/iis/configuration/system.applicationhost/sites/sitedefaults/limits)。

## <a name="see-also"></a>請參閱
- [在執行 IIS 的遠端電腦上對 ASP.NET 進行遠端偵錯](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)