---
title: 錯誤：無法啟動網頁伺服器上偵錯 |Microsoft Docs
ms.date: 05/23/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53ffc893b63447ab75a439ea1e093ddaf4b75645
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60067127"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>錯誤：無法在網頁伺服器上開始偵錯

當您嘗試偵錯 Web 伺服器上執行的 ASP.NET 應用程式時，您可能會收到這個錯誤訊息： `Unable to start debugging on the Web server`。

通常，因為發生錯誤或組態變更，需要更新您的應用程式集區、 IIS 重設，或兩者皆會發生此錯誤。 您可以開啟提升權限的命令提示字元並輸入重設 IIS `iisreset`。

## <a name="specificerrors"></a>什麼是詳細的錯誤訊息？

`Unable to start debugging on the Web server`訊息是泛型。 通常，更具體的訊息包含在錯誤字串，而且可協助您找出問題或搜尋更精確的修正程式的原因。 以下是幾個常見的錯誤訊息，附加到主要的錯誤訊息：

- [IIS 沒有列出符合啟動的網站 url](#IISlist)
- [未正確設定網頁伺服器](#web_server_config)
- [無法連接到 web 伺服器](#unabletoconnect)
- [Web 伺服器未適時回應](#webservertimeout)
- [Microsoft Visual Studio 遠端偵錯監視 (msvsmon.exe) 似乎沒有在遠端電腦上執行](#msvsmon)
- [遠端伺服器傳回錯誤](#server_error)
- [無法啟動 ASP.NET 偵錯](#aspnet)
- [偵錯工具無法連接到遠端電腦](#cannot_connect)
- [請參閱常見組態錯誤的說明。執行偵錯工具外部網頁即可提供詳細資訊。](#see_help)

## <a name="IISlist"></a> IIS 沒有列出符合啟動的網站 url

- 重新啟動 Visual Studio 系統管理員身分，然後重試 偵錯。 （某些 ASP.NET 偵錯的情況下需要提高的權限）。

    您可以設定 Visual Studio 一律系統管理員身分執行，以滑鼠右鍵按一下 Visual Studio 的捷徑圖示，選擇**屬性 > 進階**，然後選擇 永遠以系統管理員身分執行。

## <a name="web_server_config"></a> 未正確設定網頁伺服器

- 請參閱[錯誤：Web 伺服器未正確設定](../debugger/error-the-web-server-is-not-configured-correctly.md)。

## <a name="unabletoconnect"></a> 無法連接到 web 伺服器

- 是您在相同的電腦上執行 Visual Studio 和 Web 伺服器，並使用偵錯**F5** (而非**附加至處理序**)？ 開啟您專案的屬性，請確定專案已連接到正確的 Web 伺服器，並啟動 URL。 (開啟**屬性 > Web > 伺服器**或是**屬性 > 偵錯**視您的專案類型而定。 針對 Web Form 專案，開啟**屬性頁 > 起始選項 > 伺服器**。)

- 否則，重新啟動您的應用程式集區，然後重設 IIS。 如需詳細資訊，請參閱 <<c0> [ 檢查您的 IIS 設定](#vxtbshttpservererrorsthingstocheck)。

## <a name="webservertimeout"></a> Web 伺服器未適時回應

- 重設 IIS，然後重試 偵錯。 多個偵錯工具執行個體可能會附加至 IIS 處理序中;重設即加以終止。 如需詳細資訊，請參閱 <<c0> [ 檢查您的 IIS 設定](#vxtbshttpservererrorsthingstocheck)。

## <a name="msvsmon"></a> Microsoft Visual Studio 遠端偵錯監視 (msvsmon.exe) 似乎沒有在遠端電腦上執行

- 如果您正在偵錯在遠端電腦上，請確定您已[安裝且正在執行遠端偵錯工具](../debugger/remote-debugging.md)。 如果訊息中提到的防火牆，請確定[更正在防火牆中的連接埠](../debugger/remote-debugger-port-assignments.md)已開啟，特別是當您使用協力廠商防火牆。
- 如果您使用主機檔案，請確定已正確設定。 比方說，如果使用偵錯**F5** (而非**附加至處理序**)，主機檔案必須包含相同的專案 URL，您的專案屬性，如同**屬性 > Web > 伺服器**或是**屬性 > 偵錯**，取決於您的專案類型。

## <a name="server_error"></a> 遠端伺服器傳回錯誤

請檢查您[IIS 記錄檔](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0)錯誤子代碼的詳細資訊，以及此 IIS 7[部落格文章](https://blogs.iis.net/tomkmvp/troubleshoot-a-403)。

此外，以下是一些常見的錯誤碼和一些建議。
- (403) 禁止。 有許多可能的原因造成此錯誤，因此請檢查您的記錄檔和網站的 IIS 安全性設定。 請確定伺服器的 web.config 包含`debug=true`compilation 元素中。 請確定您的 Web 應用程式的資料夾具有正確的權限，並確認您的應用程式集區設定正確 （可能已變更密碼）。 請參閱[檢查您的 IIS 設定](#vxtbshttpservererrorsthingstocheck)。 如果這些設定已正確，並在本機進行偵錯，也請確認您要連接到正確的伺服器類型和 URL (在**屬性 > Web > 伺服器**或是**屬性 > 偵錯**，根據您的專案類型）。
- (503) 伺服器無法使用。 可能因為錯誤或組態變更而停止應用程式集區。 重新啟動應用程式集區。
- (404) 找不到。 請確定使用的應用程式集區設定正確的 ASP.NET 版本。

## <a name="aspnet"></a> 無法啟動 ASP.NET 偵錯

- 重新啟動應用程式集區，重設 IIS。 如需詳細資訊，請參閱 <<c0> [ 檢查您的 IIS 設定](#vxtbshttpservererrorsthingstocheck)。
- 如果您要進行 URL 重寫，測試與任何 URL 重寫的基本 web.config。 請參閱**附註**關於 URL 重寫中的模組[檢查您的 IIS 設定](#vxtbshttpservererrorsthingstocheck)。

## <a name="cannot_connect"></a> 偵錯工具無法連接到遠端電腦

如果您是在本機偵錯，因為 Visual Studio 是 32 位元應用程式，讓它使用 64 位元版本的遠端偵錯工具偵錯 64 位元應用程式，就可能會發生這個錯誤。 開啟您專案的屬性，並確定專案已設定為連線到正確的 Web 伺服器和 URL。 (開啟**屬性 > Web > 伺服器**或是**屬性 > 偵錯**視您的專案類型而定。)

此外，如果您使用主機檔案，請確定已正確設定。 比方說，主機檔案必須包含相同的專案 URL，如專案屬性中所示**屬性 > Web > 伺服器**或是**屬性 > 偵錯**，取決於您的專案類型。

## <a name="see_help"></a>參閱常見組態錯誤的說明。 執行偵錯工具外部網頁即可提供詳細資訊。

- 會在同一部電腦上執行 Visual Studio 和 Web 伺服器？ 開啟您專案的屬性，請確定專案已連接到正確的 Web 伺服器，並啟動 URL。 (開啟**屬性 > Web > 伺服器**或是**屬性 > 偵錯**視您的專案類型而定。)

- 如果仍無法解決問題，或從遠端進行偵錯，後續步驟[檢查您的 IIS 設定](#vxtbshttpservererrorsthingstocheck)。

## <a name="vxtbshttpservererrorsthingstocheck"></a> 檢查您的 IIS 設定

之後若要解決此問題，以下詳述的步驟，並再重新嘗試偵錯，您可能也需要重設 IIS。 可以這麼做，開啟提升權限的命令提示字元並輸入`iisreset`。

* 停止並重新啟動您的 IIS 應用程式集區，然後再試一次。

    應用程式集區可能因錯誤而停止。 或者，您所做的其他組態變更可能需要您停止並重新啟動您的應用程式集區。

    > [!NOTE]
    > 如果應用程式集區會停止，您可能需要從控制台解除安裝 URL Rewrite Module。 您可以使用 Web Platform Installer (WebPI) 它重新安裝。 重大系統升級之後，可能會發生此問題。

* 檢查您的應用程式集區設定、 更正它如有需要並再試一次。

    應用程式集區可能設定不符合您的 Visual Studio 專案的 ASP.NET 版本。 更新應用程式集區中的 ASP.NET 版本，然後重新啟動它。 如需詳細資訊，請參閱 < [IIS 8.0 使用 ASP.NET 3.5 和 ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)。

    此外，如果密碼認證已變更，您可能需要更新您的應用程式集區或網站。  應用程式集區中更新的認證**進階設定 > 處理序模型 > 識別**。 網站，更新的認證**基本設定 > 身分連接...**.重新啟動您的應用程式集區。

* 檢查您的 Web 應用程式的資料夾具有正確的權限。

    請確定您授與 IIS_IUSRS，IUSR，或特定使用者相關聯[應用程式集區](/iis/manage/configuring-security/application-pool-identities)讀取和執行 Web 應用程式資料夾的權限。 修正問題，然後重新啟動您的應用程式集區。

* 請確定已在 IIS 上安裝正確的 ASP.NET 版本。

    ASP.NET 在 IIS 上和您的 Visual Studio 專案中的版本不相符，可能會導致此問題。 您可能需要在 web.config 中設定的 framework 版本。若要在 IIS 上安裝 ASP.NET，請使用[Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)。 此外，請參閱[IIS 8.0 使用 ASP.NET 3.5 和 ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)或適用於 ASP.NET Core[使用 IIS 的 Windows 上的主機](https://docs.asp.net/en/latest/publishing/iis.html)。

* 若您只使用 IP 位址，請解決驗證錯誤

     根據預設，IP 位址被假設為網際網路的一部分，且不會透過網際網路完成 NTLM 驗證。 如果您的網站已設定為需要驗證的 IIS 中，此驗證將會失敗。 若要更正這個問題，您可以指定遠端電腦，而不是 IP 位址的名稱。

## <a name="other-causes"></a>其他原因

如果 IIS 設定不會造成問題，請嘗試下列步驟：

- 重新啟動 Visual Studio 系統管理員權限並再試一次。

    某些 ASP.NET 偵錯案例，例如使用 Web Deploy for Visual Studio 需要提高權限。

- 如果執行的 Visual Studio 的多個執行個體，重新開啟您的專案中 （以系統管理員權限），在 Visual studio 的一個執行個體，並再試一次。

- 如果您使用本機位址的主機檔案，請嘗試使用回送位址，而不電腦的 IP 位址。

    如果您未使用本機位址，請確定您的主機檔案包含相同的專案 URL，您的專案屬性，如同**屬性 > Web > 伺服器**或是**屬性 > 偵錯**，取決於您專案類型。

## <a name="more-troubleshooting-steps"></a>詳細的疑難排解步驟

* 顯示在瀏覽器中的伺服器上的 [localhost] 頁面。

     若 IIS 未正確安裝，則您在瀏覽器中輸入 `http://localhost` 時應該會發生錯誤。

     如需有關部署至 IIS 的詳細資訊，請參閱 < [IIS 8.0 使用 ASP.NET 3.5 和 ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)和適用於 ASP.NET Core[使用 IIS 的 Windows 上的主機](https://docs.asp.net/en/latest/publishing/iis.html)。

* 在伺服器上建立基本的 ASP.NET 應用程式 （或使用基本的 web.config 檔案）。

    如果您無法取得您的應用程式使用偵錯工具，請嘗試在伺服器上，在本機建立基本的 ASP.NET 應用程式，然後再次嘗試基本的應用程式進行偵錯。 （您可能想要使用預設 ASP.NET MVC 範本。）如果您可以偵錯的基本應用程式，可協助您識別兩個組態之間的差異。 尋找設定的差異在 web.config 檔案中，例如 URL 重寫規則。

## <a name="see-also"></a>另請參閱
- [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)