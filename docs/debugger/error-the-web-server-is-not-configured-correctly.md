---
title: "錯誤： 網頁伺服器未正確設定 |Microsoft 文件"
ms.custom: 
ms.date: 09/20/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.remote.projnotconfigured
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: debugger, Web application errors
ms.assetid: 875ba87f-c372-4126-8fe3-e33931cf26c0
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0538693a815cf9749b3cd9df007486de1af3637
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>錯誤：未正確設定 Web 伺服器

之後採取來解決問題，這裡所詳述的步驟，以及之前偵錯，請再試一次，則您可能需要重設 IIS。 您可以執行此動作開啟系統管理員命令提示字元，然後輸入`iisreset`。

執行下列步驟，解決此問題：

1. 如果伺服器上裝載的 web 應用程式設定為發行組建，而偵錯組建，以重新發行，並確認 web.config 檔案包含`debug=true`compilation 項目中。 重設 IIS，然後重試。

    例如，如果您使用發行組建的發行設定檔，將它變更為 偵錯並重新發行。 否則，將偵錯屬性設定為`false`發行時。

2. (IIS)請確認實體路徑正確。 您可以在 IIS 中，找到此設定在**基本設定 > 實體路徑**(或**進階設定**舊版 IIS 中)。

    如果 web 應用程式已複製到不同的電腦、 手動重新命名或移動，可能不正確的實體路徑。 重設 IIS，然後重試。

3. 在 Visual Studio 中，確認已選取正確的伺服器，內容中。 (開啟**屬性 > 網路 > 伺服器**或**屬性 > 偵錯**視專案類型而定。 Web Form 專案中，開啟**屬性頁 > 起始選項 > 伺服器**)。

    如果您使用的 IIS，例如外部 （自訂） 伺服器必須正確的 URL。 否則，請選取 IIS Express，然後重試。

4. (IIS)請確定正確的 ASP.NET 版本已安裝在伺服器上。

    ASP.NET 在 IIS 上和您的 Visual Studio 專案中的版本不相符，可能會導致此問題。 您可能需要在 web.config 中設定的 framework 版本。在 IIS 上安裝 ASP.NET，請使用[Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)。 此外，請參閱[IIS 8.0 使用 ASP.NET 3.5 和 ASP.NET 4.5](https://docs.microsoft.com/en-us/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)或適用於 ASP.NET Core[與 IIS 的 Windows 上的主機](https://docs.asp.net/en/latest/publishing/iis.html)。
  
4. 如果`maxConnection`限制在 IIS 中的將會過低，而您太多連線，您可能需要[增加的連線限制](https://docs.microsoft.com/en-us/iis/configuration/system.applicationhost/sites/sitedefaults/limits)。
  
## <a name="see-also"></a>另請參閱  
 [遠端偵錯遠端 IIS 電腦上的 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)   
 [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)