---
title: 錯誤：無法在 Web 服務器上啟動調試 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0b0cbd7afe90b1dbc091263e3a2594c9ca739e1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185476"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>錯誤：無法在 Web 伺服器上啟動偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您嘗試偵錯 Web 伺服器上所執行的 ASP.NET 應用程式時，您可能會收到此錯誤訊息：無法在 Web 伺服器上開始偵錯。
  
在許多情況下，因為未正確設定 IIS，所以會發生此錯誤。

## <a name="check-your-iis-configuration"></a><a name="vxtbshttpservererrorsthingstocheck"></a> 檢查您的 IIS 設定

採取步驟來解決此處詳述的問題，並在再次嘗試進行偵錯工具之前，您可能也需要重設 IIS。 您可以開啟系統管理員命令提示字元並輸入 `iisreset` ，或在 IIS 管理員中進行這項操作。 

* 請停止並重新啟動您的應用程式集區，然後重試。

    應用程式集區可能已停止，或您所做的另一種設定變更可能需要您停止並重新啟動應用程式集區。
    
    > [!NOTE]
    > 如果應用程式集區持續停止，您可能需要從主控台卸載 URL 重寫模組，然後使用 Web Platform Installer (WPI) 來重新安裝它。 這可能是重大系統升級之後的問題。

* 檢查您的應用程式集區設定，視需要加以更正，然後重試。

    如果密碼認證已變更，您可能需要在您的應用程式集區中加以更新。 此外，如果您最近安裝了 ASP.NET，則可能會針對錯誤的 ASP.NET 版本設定應用程式集區。 修正問題，並重新啟動應用程式集區。
    
* 檢查您的 Web 應用程式資料夾是否具有適當的許可權。

    請確定您提供 IIS_IUSRS 或 IUSR (或與應用程式集區相關聯的特定使用者) Web 應用程式資料夾的 [讀取] 和 [執行] 許可權。 修正問題，並重新啟動您的應用程式集區。

* 如果您使用的主機檔案具有本機位址，請嘗試使用回送位址，而不是機器的 IP 位址。

* 在瀏覽器中顯示 localhost 頁面。

     若 IIS 未正確安裝，則您在瀏覽器中輸入 `http://localhost` 時應該會發生錯誤。
     
     如需部署至 IIS 的詳細資訊，請參閱 [遠端 IIS 電腦上的遠端偵錯程式 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) ，或者，若要 ASP.NET Core，請) [發行至 iis](https://docs.asp.net/en/latest/publishing/iis.html) 。

* 請確定已在 IIS 上安裝正確版本的 ASP.NET。  請參閱 [部署 ASP.NET 應用程式](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md#BKMK_deploy_asp_net) ，或 ASP.NET Core， [發佈至 IIS](https://docs.asp.net/en/latest/publishing/iis.html)) 。

* 在伺服器上建立基本 ASP.NET 應用程式。

     如果您無法讓您的應用程式使用偵錯工具，請嘗試在伺服器本機上建立基本 ASP.NET 應用程式，並嘗試進行基本應用程式的偵錯工具。 如果您可以對基本應用程式進行偵錯工具，這可協助您識別這兩個設定之間的差異。
  
* 若您只使用 IP 位址，請解決驗證錯誤

     根據預設，IP 位址被假設為網際網路的一部分，且不會透過網際網路完成 NTLM 驗證。 如果您的網站是在 IIS 中設定為需要驗證，則此驗證將會失敗。 若要修正此問題，您可以指定遠端電腦的名稱，而不是 IP 位址。
     
## <a name="other-causes"></a>其他原因

如果您使用較舊版本的 Visual Studio：

- 以較高的許可權重新開機 Visual Studio，然後再試一次。

    較舊版本中的 bug (在某些 ASP.NET 的偵測案例中，) 需要較高的許可權。
    
- 如果有多個 Visual Studio 實例正在執行，請在 Visual Studio 的一個實例中重新開啟您的專案，然後再試一次。

## <a name="see-also"></a>另請參閱  
 [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
