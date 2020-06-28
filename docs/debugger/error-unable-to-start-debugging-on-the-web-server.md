---
title: 錯誤-無法在 Web 服務器上啟動調試 |Microsoft Docs
ms.date: 05/23/2018
ms.topic: error-reference
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
ms.openlocfilehash: 00d27dafd5e44b058cff05b3c478322e45242b3c
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460035"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>錯誤：無法在 Web 伺服器上啟動偵錯

當您嘗試在 Web 服務器上執行 ASP.NET 應用程式時，可能會收到下列錯誤訊息： `Unable to start debugging on the Web server` 。

通常會發生這個錯誤，是因為發生了需要更新應用程式集區、IIS 重設或兩者的錯誤或設定變更。 您可以開啟提升許可權的命令提示字元並輸入，以重設 IIS `iisreset` 。

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>詳細的錯誤訊息是什麼？

`Unable to start debugging on the Web server`訊息為泛型。 通常，錯誤字串中會包含更特定的訊息，並可協助您找出問題的原因，或搜尋更精確的修正程式。 以下是附加至主要錯誤訊息的一些較常見的錯誤訊息：

- [IIS 不會列出符合啟動 url 的網站](#IISlist)
- [未正確設定 Web 伺服器](#web_server_config)
- [無法連接到 web 伺服器](#unabletoconnect)
- [網頁伺服器未及時回應](#webservertimeout)
- [Microsoft Visual Studio 遠端偵錯監視 (msvsmon.exe) 似乎沒有在遠端電腦上執行](#msvsmon)
- [遠端伺服器傳回錯誤](#server_error)
- [無法啟動 ASP.NET 的調試](#aspnet)
- [偵錯工具無法連接到遠端電腦](#cannot_connect)
- [請參閱常見組態錯誤的說明。執行偵錯工具外部網頁即可提供詳細資訊。](#see_help)
- [不支援操作。未知的錯誤： *errornumber*](#operation_not_supported)

## <a name="iis-does-not-list-a-website-that-matches-the-launch-url"></a><a name="IISlist"></a>IIS 不會列出符合啟動 url 的網站

- 以系統管理員身分重新開機 Visual Studio，然後重試偵錯工具。 （有些 ASP.NET 的調試情況需要較高的許可權）。

    您可以設定 Visual Studio 一律以系統管理員身分執行，方法是以滑鼠右鍵按一下 Visual Studio 快捷方式圖示，選擇 [**屬性] > [Advanced**]，然後選擇 [一律以系統管理員身分執行]。

## <a name="the-web-server-is-not-configured-correctly"></a><a name="web_server_config"></a>未正確設定 web 伺服器

- 請參閱[錯誤：未正確設定 web 伺服器](../debugger/error-the-web-server-is-not-configured-correctly.md)。

## <a name="unable-to-connect-to-the-webserver"></a><a name="unabletoconnect"></a>無法連接到 web 伺服器

- 您是在同一部電腦上執行 Visual Studio 和 Web 服務器，並使用**F5**進行偵錯工具（而不是**附加至進程**）嗎？ 開啟專案屬性，並確定專案已設定為連接到正確的 Web 服務器並啟動 URL。 （開啟 [**屬性] > Web > 伺服器**或**屬性 >** 根據您的專案類型進行 Debug。 若為 Web form 專案，請開啟 [**屬性頁] > 啟動選項] > 伺服器**]）。

- 否則，請重新開機您的應用程式集區，然後重設 IIS。 如需詳細資訊，請參閱[檢查您的 IIS](#vxtbshttpservererrorsthingstocheck)設定。

## <a name="the-web-server-did-not-respond-in-a-timely-manner"></a><a name="webservertimeout"></a>網頁伺服器未及時回應

- 重設 IIS 並重試調試。 多個偵錯工具實例可能會附加至 IIS 進程;重設會終止它們。 如需詳細資訊，請參閱[檢查您的 IIS](#vxtbshttpservererrorsthingstocheck)設定。

## <a name="the-microsoft-visual-studio-remote-debugging-monitormsvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a><a name="msvsmon"></a>Microsoft visual studio 遠端偵錯錯監視器（msvsmon.exe）似乎未在遠端電腦上執行

- 如果您要在遠端電腦上進行偵錯工具，請確定您已[安裝，且正在執行遠端偵錯程式](../debugger/remote-debugging.md)。 如果訊息提及防火牆，請確定[防火牆中的正確埠](../debugger/remote-debugger-port-assignments.md)已開啟，特別是當您使用協力廠商防火牆時。
- 如果您使用 HOSTS 檔案，請確定它已正確設定。 例如，如果使用**F5** （而不是 [**附加至進程**]）來進行偵錯工具，則主機檔案必須包含與專案屬性相同的專案 URL， **> Web > 伺服器**] 或 [**屬性] > [Debug**]，視您的專案類型而定。

## <a name="the-remote-server-returned-an-error"></a><a name="server_error"></a>遠端伺服器傳回錯誤

檢查您的[iis 記錄](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0)檔中是否有錯誤子代碼和其他資訊，以及此 iis 7 的[blog 文章](https://blogs.iis.net/tomkmvp/troubleshoot-a-403)。

此外，以下是一些常見的錯誤碼和一些建議。
- (403) 禁止。 此錯誤有許多可能的原因，因此請檢查您的記錄檔和網站的 IIS 安全性設定。 請確定伺服器的 web.config 包含 `debug=true` 在編譯元素中。 請確定您的 Web 應用程式資料夾具有適當的許可權，且您的應用程式集區設定正確（密碼可能已經變更）。 請參閱[檢查您的 IIS](#vxtbshttpservererrorsthingstocheck)設定。 如果這些設定都是正確的，而且您要在本機進行偵錯工具，也請確認您要連接到正確的伺服器類型和 URL （在 [屬性] 中 **> Web > 伺服器**] 或 [**屬性] > [Debug**]，視您的專案類型而定）。
- (503) 伺服器無法使用。 應用程式集區可能因為錯誤或設定變更而停止。 重新開機應用程式集區。
- (404) 找不到。 請確定已針對正確的 ASP.NET 版本設定應用程式集區。

## <a name="could-not-start-aspnet-debugging"></a><a name="aspnet"></a>無法啟動 ASP.NET 的調試

- 重新開機應用程式集區並重設 IIS。 如需詳細資訊，請參閱[檢查您的 IIS](#vxtbshttpservererrorsthingstocheck)設定。
- 如果您要進行 URL 重寫，請測試不會重寫 URL 的基本 web.config。 請參閱[檢查您的 IIS](#vxtbshttpservererrorsthingstocheck)設定中的 URL 重寫模組的相關**注意事項**。

## <a name="the-debugger-cannot-connect-to-the-remote-computer"></a><a name="cannot_connect"></a>偵錯工具無法連接到遠端電腦

如果您要在本機進行偵錯工具，請在 Visual Studio 中開啟專案屬性，並確定已將專案設定為連接到正確的 Web 服務器和 URL。 （根據您的專案類型， **> Web > 伺服器**或屬性中開啟 [屬性] **> Debug** ）。

當在本機上進行偵錯工具時，可能會發生此錯誤，因為 Visual Studio 是32位的應用程式，所以它會使用64位版本的遠端偵錯程式來偵測64位應用程式。 檢查 IIS 上的應用程式集區，確定 [**啟用32位應用程式**] 已設定為 `true` 、重新開機 IIS，然後再試一次。

此外，如果您使用 HOSTS 檔案，請確定它已正確設定。 例如，視您的專案類型而定，HOSTS 檔案必須包含和專案屬性相同的專案 URL， **> Web > 伺服器**或**屬性 > Debug**。

## <a name="see-help-for-common-configuration-errors-running-the-webpage-outside-of-the-debugger-may-provide-further-information"></a><a name="see_help"></a>參閱常見組態錯誤的說明。 在偵錯工具外部執行網頁可能會提供進一步的資訊。

- 您是否在同一部電腦上執行 Visual Studio 和 Web 服務器？ 開啟專案屬性，並確定專案已設定為連接到正確的 Web 服務器並啟動 URL。 （根據您的專案類型， **> Web > 伺服器**或屬性中開啟 [屬性] **> Debug** ）。

- 如果無法運作，或您正在遠端進行偵錯工具，請遵循[檢查 IIS](#vxtbshttpservererrorsthingstocheck)設定中的步驟。

## <a name="operation-not-supported-unknown-error-errornumber"></a><a name="operation_not_supported"></a>不支援操作。 未知的錯誤： *errornumber*

如果您要進行 URL 重寫，請測試不會重寫 URL 的基本 web.config。 請參閱[檢查您的 IIS](#vxtbshttpservererrorsthingstocheck)設定中的 URL 重寫模組的相關**注意事項**。

## <a name="check-your-iis-configuration"></a><a name="vxtbshttpservererrorsthingstocheck"></a>檢查您的 IIS 設定

採取這裡詳述的步驟來解決此問題，而且在嘗試再次進行 debug 之前，您可能也需要重設 IIS。 您可以開啟提升許可權的命令提示字元並輸入來執行此動作 `iisreset` 。

* 停止並重新啟動您的 IIS 應用程式集區，然後重試。

    應用程式集區可能因錯誤而停止。 或者，您所做的另一種設定變更可能會要求您停止並重新啟動應用程式集區。

    > [!NOTE]
    > 如果應用程式集區持續停止，您可能需要從 [控制台] 卸載 [URL 重寫] 模組。 您可以使用 Web Platform Installer （WebPI）重新安裝它。 此問題可能會在大量系統升級之後發生。

* 檢查您的應用程式集區設定，如有需要請加以更正，然後再試一次。

    應用程式集區可能會針對不符合您 Visual Studio 專案的 ASP.NET 版本進行設定。 更新應用程式集區中的 ASP.NET 版本，並將它重新開機。 如需詳細資訊，請參閱[使用 ASP.NET 3.5 和 ASP.NET 4.5 的 IIS 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)。

    此外，如果密碼認證已變更，您可能需要在您的應用程式集區或網站中加以更新。  在應用程式集區中，更新 [高級設定] 中的 [認證] **> 進程模型 > 身分識別**]。 針對網站，更新 **[基本設定] 中的 [認證] > [連接**身分 ...]。重新開機您的應用程式集區。

* 檢查您的 Web 應用程式資料夾是否具有正確的許可權。

    請確定您提供 IIS_IUSRS、IUSR 或與[應用程式集](/iis/manage/configuring-security/application-pool-identities)區相關聯的特定使用者，以取得 Web 應用程式資料夾的讀取和執行許可權。 請修正問題，並重新啟動應用程式集區。

* 請確定 IIS 上已安裝正確的 ASP.NET 版本。

    IIS 和 Visual Studio 專案中的 ASP.NET 版本不相符，可能會造成此問題。 您可能需要在 web.config 中設定 framework 版本。若要在 IIS 上安裝 ASP.NET，請使用[Web Platform Installer （WebPI）](https://www.microsoft.com/web/downloads/platform.aspx)。 此外，請參閱[使用 ASP.NET 3.5 和 ASP.NET 4.5 的 IIS 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) ，或針對 ASP.NET Core，使用[iis 在 Windows 上裝載](https://docs.asp.net/en/latest/publishing/iis.html)。

* 若您只使用 IP 位址，請解決驗證錯誤

     根據預設，IP 位址被假設為網際網路的一部分，且不會透過網際網路完成 NTLM 驗證。 如果您的網站在 IIS 中設定為需要驗證，則此驗證會失敗。 若要更正此問題，您可以指定遠端電腦的名稱，而不是 IP 位址。

## <a name="other-causes"></a>其他原因

如果 IIS 設定不會造成此問題，請嘗試下列步驟：

- 請以系統管理員許可權重新開機 Visual Studio，然後再試一次。

    某些 ASP.NET 的偵錯工具案例，例如使用 Web Deploy 需要較高的 Visual Studio 許可權。

- 如果 Visual Studio 的多個實例正在執行，請在 Visual Studio 的一個實例中重新開啟您的專案（具有系統管理員許可權），然後再試一次。

- 如果您使用的主機檔案具有本機位址，請嘗試使用回送位址，而不是電腦的 IP 位址。

    如果您不是使用本機位址，請確定您的 HOSTS 檔案包含與專案屬性相同的專案 URL， **> Web > 伺服器**或**屬性 > Debug**，視您的專案類型而定。

## <a name="more-troubleshooting-steps"></a>其他疑難排解步驟

* 在伺服器上的瀏覽器中顯示 localhost 頁面。

     若 IIS 未正確安裝，則您在瀏覽器中輸入 `http://localhost` 時應該會發生錯誤。

     如需部署至 IIS 的詳細資訊，請參閱[使用 ASP.NET 3.5 和 ASP.NET 4.5 的 IIS 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) ，以及針對 ASP.NET Core，使用[iis 在 Windows 上裝載](https://docs.asp.net/en/latest/publishing/iis.html)。

* 在伺服器上建立基本的 ASP.NET 應用程式（或使用基本的 web.config 檔案）。

    如果您無法讓應用程式使用偵錯工具，請嘗試在本機伺服器上建立基本的 ASP.NET 應用程式，並嘗試對基本應用程式進行 debug。 （您可能會想要使用預設的 ASP.NET MVC 範本）。如果您可以對基本應用程式進行錯用，這可能有助於識別兩個設定之間的差異。 尋找 web.config 檔案中設定的差異，例如 URL 重寫規則。

## <a name="see-also"></a>另請參閱
- [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)