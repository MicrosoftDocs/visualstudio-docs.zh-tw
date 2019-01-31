---
title: 錯誤：Web 伺服器未正確設定 |Microsoft Docs
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
ms.openlocfilehash: fd59211da9228f2940c675f889d0536fbea9045d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55019188"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>錯誤：未正確設定 Web 伺服器

之後若要解決此問題，以下詳述的步驟，並再重新嘗試偵錯，您可能也需要重設 IIS。 可以這麼做，開啟系統管理員命令提示字元並輸入`iisreset`。

執行下列步驟以解決此問題：

1. 如果在伺服器上裝載的 web 應用程式設定為發行組建，而偵錯組建中，為重新發行，並確認 web.config 檔案包含`debug=true`compilation 元素中。 重設 IIS，然後重試。

    例如，如果您使用的發行組建的發行設定檔，將它變更為 偵錯並重新發行。 否則，將偵錯屬性設定為`false`當您將發行。

2. (IIS)確認 實體路徑正確無誤。 在 IIS 中，您會找到此設定並**基本設定 > 實體路徑**(或**進階設定**在舊版 IIS 中)。

    如果 web 應用程式已複製到不同的電腦、 手動重新命名或移動，可能不正確的實體路徑。 重設 IIS，然後重試。

3. 如果您是在本機偵錯在 Visual Studio 中，確認已選取正確的伺服器，在屬性中。 (開啟**屬性 > Web > 伺服器**或是**屬性 > 偵錯**視您的專案類型而定。 針對 Web Form 專案，開啟**屬性頁 > 起始選項 > 伺服器**)。

    如果您使用的 IIS，例如外部 （自訂） 伺服器必須正確的 URL。 否則，請選取 IIS Express，然後重試。

4. (IIS)請確定正確的 ASP.NET 版本安裝在伺服器上。

    ASP.NET 在 IIS 上和您的 Visual Studio 專案中的版本不相符，可能會導致此問題。 您可能需要在 web.config 中設定的 framework 版本。若要在 IIS 上安裝 ASP.NET，請使用[Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)。 此外，請參閱[IIS 8.0 使用 ASP.NET 3.5 和 ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)或適用於 ASP.NET Core[使用 IIS 的 Windows 上的主機](https://docs.asp.net/en/latest/publishing/iis.html)。
  
4. 如果`maxConnection`限制在 IIS 中的為太低，並有太多連線，您可能需要[增加的連線限制](/iis/configuration/system.applicationhost/sites/sitedefaults/limits)。
  
## <a name="see-also"></a>請參閱  
 [在遠端 IIS 電腦上對 ASP.NET 進行遠端偵錯](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)   
 [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)