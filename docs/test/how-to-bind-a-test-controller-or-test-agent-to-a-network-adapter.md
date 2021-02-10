---
title: 將測試控制器/測試代理程式系結至網路介面卡
description: 瞭解如何使用 IP 位址將測試控制器或測試代理程式系結至網路介面卡，以防它已安裝給多個網路介面卡。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- controllers, netwrok adapter
- agents, configuring
- agents, network adapter
- controllers, configuring
ms.assetid: 7eb9290a-f9f6-4e41-9caa-796fcfaf0610
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: f35e870e625a0f494692d082494ee0c2511ffd8f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966834"
---
# <a name="how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter"></a>如何：將測試控制器或測試代理程式繫結至網路介面卡

如果安裝測試控制器或測試代理程式軟體的電腦上有多個網路介面卡，則您必須指定 IP 位址 (而不是電腦名稱)，以識別該測試控制器或測試代理程式。

> [!WARNING]
> 當您嘗試設定測試代理程式時，可能會接收到下列錯誤：
>
> **錯誤8110。無法連接到指定的控制器電腦或存取控制器物件**
>
> 在有超過一張以上網路介面卡的電腦上安裝測試控制器，便可能導致此錯誤。 也有可能在您嘗試執行測試之前，都能夠成功安裝代理程式，而且不會看到這個問題。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="bind-a-test-controller-to-a-specific-network-adapter"></a>將測試控制器繫結至特定網路介面卡

### <a name="to-obtain-the-ip-addresses-of-the-network-adapters"></a>若要取得網路介面卡的 IP 位址

1. 在 Microsoft Windows 中選擇 [開始]，在 [開始搜尋] 方塊中鍵入 **cmd**，然後選擇 **Enter**。

2. 輸入 **ipconfig /all**。

     接著便會顯示您的網路介面卡 IP 位址。 請將控制器要繫結之網路介面卡的 IP 位址記錄下來。

### <a name="to-bind-a-network-adapter-to-a-test-controller"></a>將網路介面卡繫結至測試控制器

1. 在 Microsoft Windows 中選擇 [開始]，在 [開始搜尋] 方塊中鍵入 **services.msc**，然後選擇 **Enter**。

     [服務] 對話方塊隨即顯示。

2. 在結果窗格中的 [名稱] 資料行底下，以滑鼠右鍵按一下 [Visual Studio Test Controller] 服務，然後選擇 [停止]。

     -或-

     開啟較高權限的命令提示字元，然後在命令提示字元中執行下列命令：

     `net stop vsttcontroller`

3. 開啟位於 *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\\<edition>\Common7\IDE* 中的 *QTCcontroller.exe.config* XML 組態檔。

4. 找出 `<appSettings>` 標記。

    ```xml
    <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentConnectionTimeoutInSeconds" value="120"/>
      <add key="AgentSyncTimeoutInSeconds" value="300"/>
      <add key="ControllerServicePort" value="6901"/>
      <add key="ControllerUsersGroup" value="TeamTestControllerUsers"/>
      <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins"/>
      <add key="CreateTraceListener" value="no"/>
    </appSettings>
    ```

5. 加入 `BindTo` 索引鍵，指定要用於 `<appSettings>` 區段中的網路介面卡。

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. 啟動測試控制器服務。 若要這樣做，請在命令提示字元中執行下列命令：

    `net start vsttcontroller`

    > [!WARNING]
    > 您必須重新執行測試代理程式安裝，將測試代理程式連接到控制器。 這次請指定控制器的 IP 位址，而非控制器名稱。

     這適用於控制器、代理程式服務和代理程式處理序。 在超過一個以上網路介面卡的電腦上所執行的每一個處理序，都必須設定 `BindTo` 屬性。 這三個處理序的 `BindTo` 屬性設定程序都一樣，和本主題前面針對測試控制器所指定的設定程序相同。

### <a name="to-bind-a-network-interface-card-to-a-test-agent"></a>將網路介面卡繫結至測試代理程式

1. 在 Microsoft Windows 中選擇 [開始]，在 [開始搜尋] 方塊中鍵入 **services.msc**，然後選擇 **Enter**。

    [服務] 對話方塊隨即顯示。

2. 在結果窗格中的 [名稱] 資料行下，以滑鼠右鍵按一下 [Visual Studio Test Agent] 服務，然後選擇 [停止]。

     -或-

     開啟較高權限的命令提示字元，然後在命令提示字元中執行下列命令：

     **net stop vsttagent**

3. 開啟位於 *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\\<edition>\Common7\IDE* 中的 *QTAgentService.exe.config* XML 組態檔。

4. 找出 `<appSettings>` 標記。

    ```xml
    <appSettings>
      <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentServicePort" value="6910"/>
      <add key="ControllerConnectionPeriodInSeconds" value="30"/>
      <add key="StopTestRunCallTimeoutInSeconds" value="120"/>
      <add key="CreateTraceListener" value="no"/>
      <add key="GetCollectorDataTimeout" value="300"/>
    </appSettings>  </appSettings>
    ```

5. 加入 `BindTo` 索引鍵，指定要用於 `<appSettings>` 區段中的網路介面卡。

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. 啟動測試代理程式服務。 若要這樣做，請在命令提示字元中執行下列命令：

    `net start vsttagent`

## <a name="see-also"></a>另請參閱

- [安裝和設定測試代理程式](../test/lab-management/install-configure-test-agents.md)
- [修改負載測試記錄設定](../test/modify-load-test-logging-settings.md)
- [設定測試控制器和測試代理程式的通訊埠](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [如何：指定測試控制器和測試代理程式的超時期間](../test/how-to-specify-timeout-periods-for-test-controllers-and-test-agents.md)
