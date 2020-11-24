---
title: 設定測試控制器和測試代理程式的通訊埠
description: 瞭解如何變更測試控制器、測試代理程式和用戶端所使用的預設傳入埠，以避免與其他軟體發生衝突。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- firewalls, configuring for test agents
- firewalls, configuring for test controllers
- test agents, firewalls
- test controllers, firewalls
- agents, firewalls
- controllers, firewalls
ms.assetid: 211edbd7-9fe4-4251-ba85-8bec4363261b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2726d489c0c67bffb11bc59357f6ad107a6c94ba
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441564"
---
# <a name="configure-ports-for-test-controllers-and-test-agents"></a>設定測試控制器和測試代理程式的通訊埠

您可以變更測試控制器、測試代理程式和用戶端所使用的預設連入通訊埠。 如果您要嘗試使用測試控制器、測試代理程式或用戶端搭配與通訊埠設定衝突的其他某些軟體，這可能就是必要的動作。 其他變更通訊埠的原因是測試控制器與用戶端之間的防火牆限制。 在此情況下，您可能會想要手動設定要納入的通訊埠，以便針對防火牆啟用此通訊埠，讓測試控制器能夠將結果傳送至用戶端。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

下圖顯示測試控制器、測試代理程式與用戶端之間的連接點。 本文將概述哪些通訊埠會用於連入和連出連線，以及這些通訊埠所使用的安全性限制。

![測試控制器和測試代理程式的通訊埠與安全性](../test/media/test-controller-agent-firewall.png)

## <a name="incoming-connections"></a>連入連線

測試控制器所使用的預設通訊埠是 6901，而測試代理程式的預設通訊埠是 6910。 根據預設，用戶端會使用隨機通訊埠，從測試控制器接收測試結果。 對於所有連入連線，測試控制器會驗證呼叫方並確認它是否屬於特定安全性群組。

- **測試控制器** 連入連線位於 TCP 通訊埠 6901 上。 如果需要的話，您可以設定連入通訊埠。 如需詳細資訊，請參閱[設定連入通訊埠](#configure-the-incoming-ports)。

    測試控制器必須能夠建立測試代理程式和用戶端的連出連線。

    > [!NOTE]
    > 測試控制器需要將 [檔案及印表機共用] 連入連線保持在開啟狀態。

- **測試代理程式** 連入連線位於 TCP 通訊埠 6910 上。 如果需要的話，您可以設定連入通訊埠。 如需詳細資訊，請參閱[設定連入通訊埠](#configure-the-incoming-ports)。

   測試代理程式必須能夠建立測試控制器的連出連線。

- **用戶端** 根據預設，隨機 TCP 通訊埠會用於連入連線。 如果需要的話，您可以設定連入通訊埠。 如需詳細資訊，請參閱[設定連入通訊埠](#configure-the-incoming-ports)。

   當測試控制器第一次嘗試連接至用戶端時，您可能會收到防火牆通知。

   在 Windows Server 2008 上，防火牆通知預設為停用，而且您必須手動針對用戶端程式 (*devenv.exe*、*mstest.exe* 和 *mlm.exe*) 新增防火牆例外狀況，才能讓系統接受連入連線。

## <a name="outgoing-connections"></a>傳出連線

隨機 TCP 通訊埠會用於所有連出連線。

- **測試控制器** 測試控制器必須能夠建立代理程式和用戶端的連出連線。

- **測試代理程式** 測試代理程式必須能夠建立控制器的連出連線。

- **用戶端** 用戶端必須能夠建立控制器的連出連線。

## <a name="configure-the-incoming-ports"></a>設定連入通訊埠

依照這些指示設定測試控制器和測試代理程式的通訊埠。

- **控制器服務** 請編輯 *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config* 檔案來修改通訊埠的值：

    ```xml
    <appSettings>
      <add key="ControllerServicePort" value="6901"/>
    </appSettings>
    ```

- **代理程式服務** 請編輯 *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTAgentService.exe.config* 檔案來修改通訊埠：

    ```xml
    <appSettings>
      <add key="AgentServicePort" value="6910"/>
    </appSettings>
    ```

- **用戶端** 請使用登錄編輯程式來新增下列登錄 (**DWORD**) 值。 用戶端將會使用指定之範圍內的其中一個通訊埠來接收測試控制器的資料：

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeStart**

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeEnd**

## <a name="see-also"></a>另請參閱

- [安裝和設定測試代理程式](../test/lab-management/install-configure-test-agents.md)
