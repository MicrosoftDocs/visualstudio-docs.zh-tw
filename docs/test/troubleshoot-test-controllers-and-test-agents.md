---
title: 針對測試控制器和測試代理程式進行移難排解
description: 瞭解當您在 Visual Studio 中使用測試控制器和測試代理程式時，可能會遇到的一些常見問題。
ms.custom: SEO-VS-2020
ms.date: 10/20/2016
ms.topic: troubleshooting
helpviewer_keywords:
- load tests, test controllers
- load tests, troubleshooting
- load tests, test agents
- troubleshooting, test controllers and agents in load tests
ms.assetid: 77329348-3a5d-43de-b6cb-90f93296a081
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 8d9cae19736c9578f812e5e5fcd60dd9c6092e96
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838278"
---
# <a name="strategies-for-troubleshooting-test-controllers-and-test-agents-in-load-tests"></a>負載測試中測試控制器和測試代理程式的疑難排解策略

本文說明當您在 Visual Studio 中使用測試控制器和測試代理程式時，可能會遇到的一些常見問題。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="unable-to-collect-performance-counters-on-test-agent-computer"></a>無法收集測試代理程式電腦上的效能計數器

當您執行負載測試時，若您嘗試連接至測試代理程式電腦並收集效能計數器，便可能會接收到錯誤。 「遠端登錄」服務是負責提供效能計數器資料給遠端電腦的服務。 在某些作業系統上，遠端登錄服務並不會自動啟動。 若要修正此問題，請手動啟動「遠端登錄」服務。

> [!NOTE]
> 您可以在 [控制台] 中存取「遠端登錄」服務。 選擇 [系統管理工具]，然後選擇 [服務]。

造成這個問題的另一個原因，是您沒有讀取效能計數器的足夠權限。 對於本機測試回合，執行測試的使用者帳戶必須是 [Power Users] 群組 (或更高) 的成員，或 [Performance Monitor Users] 群組的成員。 對於遠端測試回合，設定控制器執行的帳戶必須是 [Power Users] 群組 (或更高) 的成員，或 [Performance Monitor Users] 群組的成員。

## <a name="set-the-logging-level-on-a-test-controller-computer"></a>設定測試控制器電腦上的記錄層次

您可以在測試控制器電腦上控制記錄層次。 當您針對在環境上執行負載測試所發生的問題嘗試加以診斷時，這便很有用。

### <a name="to-set-the-logging-level-on-a-test-controller-computer"></a>若要設定測試控制器電腦上的記錄層次

1. 停止測試控制器服務。 在命令提示中，鍵入 `net stop vsttcontroller`。

2. 開啟 *QTController.exe.config* 的檔案。此檔案位於控制器安裝目錄中。

3. 在該檔案的系統診斷區段中，編輯 `EqtTraceLevel` 參數的項目。 您的程式碼應該會與以下相似：

    ```xml
    <system.diagnostics>
        <trace autoflush="true" indentsize="4">
            <listeners>
                <add name="myListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="d:\VSTestHost.log" />
            </listeners>
        </trace>
        <switches>
            <!-- You must use integral values for "value":
                    0 = off,
                    1 = error,
                    2 = warn,
                    3 = info,
                    4 = verbose. -->
            <add name="EqtTraceLevel" value="4" />
        </switches>
    </system.diagnostics>
    ```

4. 儲存檔案。

5. 啟動控制器服務。 在命令提示中，鍵入 `net start vsttcontroller`。

這適用於測試控制器、測試代理程式服務和測試代理程式處理序。 在診斷問題時，啟用記錄以記錄這三個處理序，是很有用的做法。 這三個處理序的記錄層次設定程序都一樣，和前述針對測試控制器所指定的設定程序相同。 若要設定測試代理程式服務和代理程式處理序的記錄層次，請使用下列組態檔：

- *QTController.exe.config* 控制器服務

- *QTAgentService.exe.config* 代理程式服務

- *QTDCAgent(32).exe.config* 用於 32 位元架構的代理程式資料配接器處理序。

- *QTDCAgent(64).exe.config* 用於 64 位元架構的代理程式資料配接器處理序。

- *QTAgent(32).exe.config* 用於 32 位元架構的代理程式測試處理序。

- *QTAgent(64).exe.config* 用於 64 位元架構的代理程式測試處理序。

## <a name="bind-a-test-controller-to-a-network-adapter"></a>將測試控制器繫結至網路介面卡

當您嘗試設定測試代理程式時，可能會接收到下列錯誤：

**錯誤8110。無法連接到指定的控制器電腦或存取控制器物件。**

在有超過一張以上網路介面卡的電腦上安裝測試控制器，便可能導致此錯誤。

> [!NOTE]
> 另一個可能的情況是，您安裝測試代理程式成功，並在執行測試之前，都不會看到這個問題。

若要修正此錯誤，您必須將測試控制器繫結至其中一張網路介面卡。 您必須在測試控制器上設定 `BindTo` 屬性，然後變更測試代理程式以根據 IP 位址 (而非名稱) 參考至測試控制器。 請依下列程序的步驟執行。

### <a name="to-obtain-the-ip-address-of-the-network-adapter"></a>取得網路介面卡的 IP 位址

1. 選擇 [ **開始**]，然後選擇 [ **執行**]。

     [執行] 對話方塊隨即顯示。

2. 鍵入 `cmd`，然後選擇 [確定]。

     命令提示字元隨即開啟。

3. 輸入 `ipconfig /all`。

     接著便會顯示您的網路介面卡 IP 位址。 請將控制器要繫結之網路介面卡的 IP 位址記錄下來。

### <a name="to-bind-a-test-controller-to-a-network-adapter"></a>若要將測試控制器繫結至網路介面卡

1. 停止測試控制器服務。 在命令提示中，鍵入 `net stop vsttcontroller`。

2. 開啟 *QTController.exe.config* 的檔案。這個檔案位於 *% ProgramFiles (x86) % \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE*。

3. 將 `BindTo` 屬性的項目加入至應用程式設定。 指定控制器要繫結之網路介面卡的 IP 位址。 您的程式碼應該會與以下相似：

    ```xml
    <appSettings>
        <add key="LogSizeLimitInMegs" value="20" />
        <add key="AgentSyncTimeoutInSeconds" value="120" />
        <add key="ControllerServicePort" value="6901" />
        <add key="ControllerUsersGroup" value="TeamTestControllerUsers" />
        <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins" />
        <add key="CreateTraceListener" value="no" />
        <add key="BindTo" value="<YOUR IP ADDRESS>" />
    </appSettings>
    ```

4. 儲存檔案。

5. 啟動測試控制器服務。 在命令提示中，鍵入 `net start vsttcontroller`。

### <a name="to-connect-a-test-agent-to-a-bound-controller"></a>將測試代理程式連接至繫結控制器

- 再次安裝測試代理程式。 這次請指定測試控制器的 IP 位址，而非測試控制器名稱。

這適用於測試控制器、測試代理程式服務和測試代理程式處理序。 在超過一個以上網路介面卡的電腦上所執行的每一個處理序，都必須設定 `BindTo` 屬性。 這三個處理序的 `BindTo` 屬性設定程序都一樣，和前述針對測試控制器所指定的設定程序相同。 若要設定測試代理程式服務與測試代理程式處理序的記錄層次，請使用[在測試控制器電腦上設定記錄層次](#set-the-logging-level-on-a-test-controller-computer)中列出的組態檔。

## <a name="see-also"></a>另請參閱

- [測試控制器和測試代理程式](../test/configure-test-agents-and-controllers-for-load-tests.md)
