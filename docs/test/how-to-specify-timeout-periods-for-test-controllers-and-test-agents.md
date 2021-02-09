---
title: 測試控制器和測試代理程式的逾時期間
description: 藉由編輯相關聯的 XML 設定檔，瞭解如何變更測試控制器和測試代理程式的超時值。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- agents, configuring
- agetns, timeouts
- controllers, configuring
- controllers, timeouts
ms.assetid: 777d0db5-0073-458a-a2a3-58b1c1f24c60
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 3cca59fc165871e24269723635a1393d2f859178
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879562"
---
# <a name="how-to-specify-timeout-periods-for-test-controllers-and-test-agents"></a>如何：指定測試控制器和測試代理程式的逾時期限

測試控制器和測試代理程式都有數個逾時設定，指定發生錯誤而失敗之前應該等候彼此回應或資料來源回應的時間。 在某些情況下，可能需要編輯逾時值，以符合您的拓撲需求或解決其他環境問題。 若要編輯逾時值，請編輯與測試控制器或測試代理程式相關聯的 XML 組態檔，如下列程序所示。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

若要編輯測試控制器或測試代理程式的各種逾時設定，請使用下表中的機碼名稱和值修改下列組態檔：

- 測試控制器：*QTController.exe.config*

    |索引鍵名稱|描述|值|
    |-|-----------------|-|
    |AgentConnectionTimeoutInSeconds|在連接被視為遺失之前候代理程式 Ping 要求的秒數。|"n" 秒。|
    |AgentSyncTimeoutInSeconds|當您啟動同步處理的測試回合時，在中止回合之前等候所有代理程式同步的秒數。|"n" 秒。|
    |AgentInitializeTimeout|在中止測試回合之前，等候所有代理程式及其資料收集器於測試回合開始時初始化的秒數。 如果使用資料收集器，這個值應該適度大。|"n" 秒。 預設值："120" (2 分鐘)。|
    |AgentCleanupTimeout|在完成測試回合之前等候所有代理程式及其資料收集器清除的秒數。 如果使用資料收集器，這個值應該適度大。|"n" 秒。 預設值："120" (2 分鐘)。|

- 測試代理程式：*QTAgentService.exe.config*

    |索引鍵名稱|描述|值|
    |-|-----------------|-|
    |ControllerConnectionPeriodInSeconds|對控制器之連接嘗試的相隔秒數。|"n" 秒。 預設值："30" (30 秒)。|
    |RemotingTimeoutSeconds|遠端呼叫可存留的最大時間 (以秒為單位)。|"n" 秒。 預設值："600" (10 分鐘)。|
    |StopTestRunCallTimeoutInSeconds|等候呼叫停止測試回合的秒數。|"n" 秒。 預設值："120" (2 分鐘)。|
    |GetCollectorDataTimeout|等候資料收集器的秒數。|"n" 秒。 預設值："300" (5 分鐘)。|

## <a name="to-specify-agent-timeout-options-for-a-test-controller"></a>指定測試控制器的代理程式逾時選項

1. 開啟位於 *% ProgramFiles (x86) % \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE* 的 *QTCcontroller.exe.config* XML 設定檔。

2. 找出 `<appSettings>` 標記。

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

3. 編輯測試控制器其中一個逾時機碼的現有值。 例如，您可以將 `AgentConnectionTimeoutInSeconds` 機碼的預設值從兩分鐘變更為三分鐘：

    ```xml
    <add key="AgentConnectionTimeoutInSeconds" value="180"/>
    ```

    -或-

    加入其他機碼並指定逾時值。 例如，您可以在 `AgentInitializeTimeout` 區段中加入 `<appSettings>` 機碼並指定值為五分鐘：

    ```xml
    <appSettings>
            <add key="AgentInitializeTimeout" value="300"/>
    </appSettings>
    ```

## <a name="to-specify-agent-timeout-options-for-a-test-agent"></a>指定測試代理程式的代理程式逾時選項

1. 開啟位於 *% ProgramFiles (x86) % \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE* 的 *QTAgentService.exe.config* XML 設定檔。

2. 找出 `<appSettings>` 標記。

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

3. 編輯測試代理程式其中一個逾時機碼的現有值。 例如，您可以將 `ControllerConnectionPeriodInSeconds` 機碼的預設值從 30 秒變更為一分鐘：

    ```xml
    <add key="ControllerConnectionPeriodInSeconds" value="60"/>
    ```

    -或-

    加入其他機碼並指定逾時值。 例如，您可以在 `RemotingTimeoutSeconds` 區段中加入 `<appSettings>` 機碼並指定值為 15 分鐘：

    ```xml
    <appSettings>
            <add key=" RemotingTimeoutSeconds " value="900"/>
    </appSettings>
    ```

## <a name="see-also"></a>另請參閱

- [安裝和設定測試代理程式](../test/lab-management/install-configure-test-agents.md)
- [修改負載測試記錄設定](../test/modify-load-test-logging-settings.md)
- [設定測試控制器和測試代理程式的通訊埠](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [如何：將測試控制器或測試代理程式繫結至網路介面卡](../test/how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter.md)
