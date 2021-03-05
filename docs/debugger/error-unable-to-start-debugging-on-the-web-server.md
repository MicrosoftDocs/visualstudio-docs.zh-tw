---
description: 當您嘗試在 Web 服務器上執行 ASP.NET 應用程式的偵錯工具時，可能會收到下列錯誤訊息：無法在 Web 服務器上啟動偵錯工具。
title: 無法在 Web 服務器上啟動調試 |Microsoft 檔
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 91fa3f74c5dd0f5f6a036d5da7a779e68462c426
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146362"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>錯誤：無法在 Web 伺服器上啟動偵錯

當您嘗試在 Web 服務器上執行 ASP.NET 應用程式的偵錯工具時，可能會收到下列錯誤訊息： `Unable to start debugging on the Web server` 。

通常會發生這個錯誤，因為發生錯誤或設定變更，需要更新您的應用程式集區、IIS 重設或兩者。 您可以開啟提升許可權的命令提示字元並輸入，以重設 IIS `iisreset` 。

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>詳細的錯誤訊息為何？

此 `Unable to start debugging on the Web server` 訊息為泛型。 通常，錯誤字串中會包含更明確的訊息，並可協助您找出問題的原因，或搜尋更精確的修正程式。 以下是幾個較常見的錯誤訊息，這些訊息會附加至主要錯誤訊息：

- [IIS 不會列出符合啟動 url 的網站](#IISlist)
- [未正確設定 Web 伺服器](#web_server_config)
- [無法連接到 web 伺服器](#unabletoconnect)
- [Web 服務器未及時回應](#webservertimeout)
- [Microsoft Visual Studio 遠端偵錯監視 (msvsmon.exe) 似乎沒有在遠端電腦上執行](#msvsmon)
- [遠端伺服器傳回錯誤](#server_error)
- [無法啟動 ASP.NET 調試](#aspnet)
- [偵錯工具無法連接到遠端電腦](#cannot_connect)
- [請參閱常見組態錯誤的說明。執行偵錯工具外部網頁即可提供詳細資訊。](#see_help)
- [不支援操作。未知的錯誤： *errornumber*](#operation_not_supported)

## <a name="iis-does-not-list-a-website-that-matches-the-launch-url"></a><a name="IISlist"></a> IIS 不會列出符合啟動 url 的網站

- 以系統管理員身分重新開機 Visual Studio，然後重試一次偵錯工具。  (某些 ASP.NET 的偵測情節需要較高的許可權。 ) 

    您可以將 Visual Studio 設定為一律以系統管理員身分執行，方法是以滑鼠右鍵按一下 Visual Studio 快捷方式圖示，選擇 [ **屬性] > [Advanced**]，然後選擇 [一律以系統管理員身分執行]。

## <a name="the-web-server-is-not-configured-correctly"></a><a name="web_server_config"></a> 未正確設定 web 伺服器

- 請參閱 [錯誤：未正確設定 web 伺服器](../debugger/error-the-web-server-is-not-configured-correctly.md)。

## <a name="unable-to-connect-to-the-webserver"></a><a name="unabletoconnect"></a> 無法連接到 web 伺服器

- 您是否在同一部電腦上執行 Visual Studio 和 Web 服務器，並使用 **F5** (而不是 **附加至進程**) ？ 開啟您的專案屬性，並確定已將專案設定為連接到正確的 Web 服務器並啟動 URL。 根據您的專案類型， (開啟 [ **Web > 伺服器** ] 或 [屬性] > **> Debug** 。 若為 Web form 專案，請開啟 [ **屬性頁] > 啟動選項 > Server**]。 ) 

- 否則，請重新開機您的應用程式集區，然後重設 IIS。 如需詳細資訊，請參閱 [檢查您的 IIS](#vxtbshttpservererrorsthingstocheck)設定。

## <a name="the-web-server-did-not-respond-in-a-timely-manner"></a><a name="webservertimeout"></a> Web 服務器未及時回應

- 重設 IIS 並重試調試。 多個偵錯工具實例可能附加至 IIS 進程;重設會終止它們。 如需詳細資訊，請參閱 [檢查您的 IIS](#vxtbshttpservererrorsthingstocheck)設定。

## <a name="the-microsoft-visual-studio-remote-debugging-monitormsvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a><a name="msvsmon"></a> Microsoft visual studio 遠端偵錯 (msvsmon.exe) 似乎未在遠端電腦上執行

- 如果您是在遠端電腦上進行偵錯工具，請確定您已 [安裝且正在執行遠端偵錯程式](../debugger/remote-debugging.md)。 如果訊息提及防火牆，請確定已開啟 [防火牆中的正確埠](../debugger/remote-debugger-port-assignments.md) ，特別是當您使用協力廠商防火牆時。
- 如果您使用 HOSTS 檔案，請確定已正確設定。 例如，如果使用 **F5** 進行偵錯工具 (而不是 **附加至進程**) ，主機檔案就必須在您的專案屬性中包含相同的專案 URL、根據您的專案類型 **> Web > 伺服器** 或 **屬性 >** 的屬性。

## <a name="the-remote-server-returned-an-error"></a><a name="server_error"></a> 遠端伺服器傳回錯誤

檢查您的 [iis 記錄](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0) 檔中是否有錯誤子代碼和其他資訊，以及這篇 iis 7 的 [blog 文章](https://blogs.iis.net/tomkmvp/troubleshoot-a-403)。

此外，以下是一些常見的錯誤碼和一些建議。
- (403) 禁止。 此錯誤有許多可能的原因，因此請檢查您的記錄檔和網站的 IIS 安全性設定。 請確定伺服器的 web.config 包含 `debug=true` 在編譯元素中。 請確定您的 Web 應用程式資料夾具有正確的許可權，而且您的應用程式集區設定正確 (密碼可能已變更) 。 請參閱 [檢查您的 IIS](#vxtbshttpservererrorsthingstocheck)設定。 如果這些設定都是正確的，而且您是在本機上進行偵錯工具，也請確認您是根據專案類型) ，在 [ **> Web > 伺服器** ] 或 [ **> 屬性**] (的 [屬性] 中，連接到正確的伺服器類型和 URL。
- (503) 伺服器無法使用。 應用程式集區可能因為錯誤或設定變更而停止。 重新開機應用程式集區。
- (404) 找不到。 請確定應用程式集區已設定正確的 ASP.NET 版本。

## <a name="could-not-start-aspnet-debugging"></a><a name="aspnet"></a> 無法啟動 ASP.NET 調試

- 重新開機應用程式集區，並重設 IIS。 如需詳細資訊，請參閱 [檢查您的 IIS](#vxtbshttpservererrorsthingstocheck)設定。
- 如果您正在重寫 URL，請測試不含 URL 重寫的基本 web.config。 請參閱 [檢查 IIS](#vxtbshttpservererrorsthingstocheck)設定中有關 URL 重寫模組的 **注意事項**。

## <a name="the-debugger-cannot-connect-to-the-remote-computer"></a><a name="cannot_connect"></a> 偵錯工具無法連接到遠端電腦

如果您要在本機進行偵錯工具，請在 Visual Studio 中開啟您的專案屬性，並確定已將專案設定為連接到正確的 Web 服務器和 URL。 根據您的專案類型， (開啟 [ **Web > 伺服器** ] 或 [屬性] > **> Debug** 。 ) 

當您在本機上進行偵錯工具時，可能會發生這個錯誤，因為 Visual Studio 是32位的應用程式，因此它會使用64位版本的遠端偵錯程式來將64位應用程式進行偵錯工具。 檢查 IIS 上的應用程式集區，以確定 [ **啟用32位應用程式** ] 已設定為 `true` 、重新開機 IIS，然後再試一次。

此外，如果您使用 HOSTS 檔案，請確定已正確設定。 例如，HOSTS 檔案必須包含與您的專案屬性相同的專案 URL， **> Web > 伺服器** 或屬性（property）， **> Debug**（視您的專案類型而定）。

## <a name="see-help-for-common-configuration-errors-running-the-webpage-outside-of-the-debugger-may-provide-further-information"></a><a name="see_help"></a>參閱常見組態錯誤的說明。 在偵錯工具外部執行網頁可能會提供進一步的資訊。

- 您是否在同一部電腦上執行 Visual Studio 和 Web 服務器？ 開啟您的專案屬性，並確定已將專案設定為連接到正確的 Web 服務器並啟動 URL。 根據您的專案類型， (開啟 [ **Web > 伺服器** ] 或 [屬性] > **> Debug** 。 ) 

- 如果無法運作或您正在遠端進行遠端處理，請依照 [檢查 IIS](#vxtbshttpservererrorsthingstocheck)設定中的步驟操作。

## <a name="operation-not-supported-unknown-error-errornumber"></a><a name="operation_not_supported"></a> 不支援操作。 未知的錯誤： *errornumber*

如果您正在重寫 URL，請測試不含 URL 重寫的基本 web.config。 請參閱 [檢查 IIS](#vxtbshttpservererrorsthingstocheck)設定中有關 URL 重寫模組的 **注意事項**。

## <a name="check-your-iis-configuration"></a><a name="vxtbshttpservererrorsthingstocheck"></a> 檢查您的 IIS 設定

當您採取詳細步驟來解決問題，並在再次嘗試進行調試之前，您可能也需要重設 IIS。 您可以開啟提升許可權的命令提示字元並輸入 `iisreset` 。

* 請停止並重新啟動 IIS 應用程式集區，然後再試一次。

    由於發生錯誤，應用程式集區可能已停止。 或者，您所做的另一種設定變更可能需要您停止並重新啟動應用程式集區。

    > [!NOTE]
    > 如果應用程式集區持續停止，您可能需要從 [控制台] 卸載 URL 重寫模組。 您可以使用 (WebPI) 的 Web Platform Installer 重新安裝它。 這項問題可能會在重要的系統升級後發生。

* 檢查您的應用程式集區設定，視需要加以更正，然後重試。

    您可以針對不符合 Visual Studio 專案的 ASP.NET 版本，設定應用程式集區。 更新應用程式集區中的 ASP.NET 版本，然後重新開機它。 如需詳細資訊，請參閱 [使用 ASP.NET 3.5 和 ASP.NET 4.5 的 IIS 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)。

    此外，如果密碼認證已變更，您可能需要在您的應用程式集區或網站中加以更新。  在應用程式集區中，更新 [ **Advanced Settings] > 進程模型 > 身分識別** 的認證。 針對網站，在 [ **基本設定]** 中更新認證 > 連接身分 ...]。重新開機您的應用程式集區。

* 檢查您的 Web 應用程式資料夾是否具有適當的許可權。

    請確定您提供 IIS_IUSRS、IUSR 或特定使用者與 Web 應用程式資料夾的 [應用程式集](/iis/manage/configuring-security/application-pool-identities) 區讀取和執行許可權相關聯。 修正問題，並重新啟動您的應用程式集區。

* 請確定已在 IIS 上安裝正確版本的 ASP.NET。

    IIS 和 Visual Studio 專案中的 ASP.NET 版本不相符，可能會造成此問題。 您可能需要在 web.config 中設定 framework 版本。若要在 IIS 上安裝 ASP.NET，請使用 [ (WebPI) 的 Web Platform Installer ](https://www.microsoft.com/web/downloads/platform.aspx)。 此外，請參閱 [使用 ASP.NET 3.5 和 ASP.NET 4.5 的 IIS 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) ，或針對 ASP.NET Core， [在 WINDOWS 上使用 iis 裝載](https://docs.asp.net/en/latest/publishing/iis.html)。

* 若您只使用 IP 位址，請解決驗證錯誤

     根據預設，IP 位址被假設為網際網路的一部分，且不會透過網際網路完成 NTLM 驗證。 如果您的網站在 IIS 中設定為需要驗證，則此驗證會失敗。 若要修正此問題，您可以指定遠端電腦的名稱，而不是 IP 位址。

## <a name="other-causes"></a>其他原因

如果 IIS 設定未造成問題，請嘗試下列步驟：

- 以系統管理員許可權重新開機 Visual Studio，然後再試一次。

    某些 ASP.NET 的偵錯工具（例如使用 Web Deploy）需要較高的 Visual Studio 許可權。

- 如果有多個 Visual Studio 實例正在執行中，請在 Visual Studio (中重新開啟您的專案，並) 系統管理員許可權，然後再試一次。

- 如果您使用的主機檔案具有本機位址，請嘗試使用回送位址，而不是機器的 IP 位址。

    如果您不是使用本機位址，請確定您的 HOSTS 檔案包含與您的專案屬性相同的專案 URL， **> Web > 伺服器** 或 **屬性 > Debug**（視您的專案類型而定）。

## <a name="more-troubleshooting-steps"></a>更多疑難排解步驟

* 在伺服器上的瀏覽器中顯示 localhost 頁面。

     若 IIS 未正確安裝，則您在瀏覽器中輸入 `http://localhost` 時應該會發生錯誤。

     如需部署至 IIS 的詳細資訊，請參閱 [使用 ASP.NET 3.5 和 ASP.NET 4.5 的 iis 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) ，以及適用于 ASP.NET Core、 [在 WINDOWS 上使用 iis 的主機](https://docs.asp.net/en/latest/publishing/iis.html)。

* 在伺服器上建立基本 ASP.NET 應用程式 (或使用基本的 web.config 檔) 。

    如果您無法讓您的應用程式使用偵錯工具，請嘗試在伺服器本機上建立基本 ASP.NET 應用程式，並嘗試進行基本應用程式的偵錯工具。  (您可能會想要使用預設的 ASP.NET MVC 範本。 ) 如果您可以對基本應用程式進行偵錯工具，就可以協助您找出這兩個設定之間的差異。 尋找 web.config 檔案中設定的差異，例如 URL 重寫規則。

## <a name="see-also"></a>另請參閱
- [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
