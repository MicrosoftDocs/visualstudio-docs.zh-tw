---
title: 錯誤： 無法啟動網頁伺服器上偵錯 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- IIS, debugging DLLs
- debugger, Web application errors
- unable to start debugging error
- security [debugger], Web applications
- debugging [Visual Studio], errors
- HTTP servers, debugging error
- security settings, checking for default Web sites
- errors [debugger], unable to start debugging
- debugging ASP.NET Web applications, unable to start debugging error
- remote debugging, errors
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 40
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ccfce76d1cedacecdc467971151a6f9a66d5af68
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49217876"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>錯誤：無法在 Web 伺服器上啟動偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您嘗試偵錯 Web 伺服器上所執行的 ASP.NET 應用程式時，您可能會收到此錯誤訊息：無法在 Web 伺服器上開始偵錯。
  
在許多情況下，因為 IIS 未正確設定，就會發生此錯誤。

##  <a name="vxtbshttpservererrorsthingstocheck"></a> 檢查您的 IIS 設定

之後採取來解決問題，並再重新嘗試偵錯的詳細步驟，您可能也需要重設 IIS。 可以這麼做，開啟系統管理員命令提示字元並輸入`iisreset`，或您可以在 [IIS 管理員] 中。 

* 停止並重新啟動您的應用程式集區，然後再試一次。

    應用程式集區可能已停止，或另一個您所做的組態變更可能需要您停止並重新啟動您的應用程式集區。
    
    > [!NOTE]
    > 如果應用程式集區會停止，您可能需要從控制台解除安裝 URL Rewrite Module，然後再重新安裝使用 Web Platform Installer (WPI)。 重大系統升級之後，這可能是問題。

* 檢查您的應用程式集區設定、 更正它如有需要並再試一次。

    如果密碼認證已變更，您可能需要更新這些應用程式集區中。 此外，如果您最近已安裝 ASP.NET，應用程式集區可能設定的 ASP.NET 版本錯誤。 修正問題，然後重新啟動應用程式集區。
    
* 檢查您的 Web 應用程式的資料夾具有正確的權限。

    請確定您授與 IIS_IUSRS 或 IUSR （或特定應用程式集區相關聯的使用者） 讀取和執行 Web 應用程式資料夾的權限。 修正問題，然後重新啟動您的應用程式集區。

* 如果您使用本機位址的主機檔案，請嘗試使用回送位址，而不電腦的 IP 位址。

* 啟動瀏覽器中的 [localhost] 頁面。

     若 IIS 未正確安裝，則您在瀏覽器中輸入 `http://localhost` 時應該會發生錯誤。
     
     如需部署至 IIS 的相關資訊，請參閱[Remote Debugging ASP.NET on a Remote IIS Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)或適用於 ASP.NET Core [Publishing to IIS](https://docs.asp.net/en/latest/publishing/iis.html))。

* 請確定已在 IIS 上安裝正確的 ASP.NET 版本。  請參閱[部署 ASP.NET 應用程式](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md#BKMK_deploy_asp_net)或適用於 ASP.NET Core [Publishing to IIS](https://docs.asp.net/en/latest/publishing/iis.html))。

* 在伺服器上建立基本的 ASP.NET 應用程式。

     如果您無法取得您的應用程式使用偵錯工具，請嘗試在伺服器上，在本機建立基本的 ASP.NET 應用程式，然後再次嘗試基本的應用程式進行偵錯。 如果您可以偵錯的基本應用程式，可協助您識別兩個組態之間的差異。
  
* 若您只使用 IP 位址，請解決驗證錯誤

     根據預設，IP 位址被假設為網際網路的一部分，且不會透過網際網路完成 NTLM 驗證。 如果您的網站已設定為需要驗證的 IIS 中，此驗證會失敗。 若要更正這個問題，您可以指定遠端電腦，而不是 IP 位址的名稱。
     
## <a name="other-causes"></a>其他原因

如果您使用較舊版本的 Visual Studio:

- 使用提高的權限重新啟動 Visual Studio 並再試一次。

    （稍後修正） 的較舊版本中的 bug 需要提高的權限中有些 ASP.NET 偵錯案例。
    
- 如果執行的 Visual Studio 的多個執行個體，重新開啟您的專案中的 Visual Studio 中，一個執行個體，並再試一次。
   
  
## <a name="see-also"></a>另請參閱  
 [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



