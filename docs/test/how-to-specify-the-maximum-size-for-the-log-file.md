---
title: Visual Studio 中負載測試的記錄檔大小 | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, logging
ms.assetid: 417059bf-37ae-4e7a-b9b0-29bd71f1414f
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 92f9843c36889c77ff0f18e79289f9a749e879b1
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-specify-the-maximum-size-for-the-log-file-for-load-tests"></a>如何：指定負載測試的記錄檔大小上限

根據預設，用於負載測試之記錄檔的大小上限設定為 20 MB。 您可以透過編輯與控制器服務建立關聯的組態檔，來變更這個值。

## <a name="specify-the-maximum-log-file-size-for-load-test"></a>指定負載測試的記錄檔大小上限

1.  開啟位於 %ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config 中的 *QTCcontroller.exe.config* XML 組態檔。

2.  在 `<add key="LogSizeLimitInMegs" value="20"/>` 標籤底下找出 `<appSettings>` 項目。

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

3.  將 `value ="20"` 修改成您想要針對記錄檔指定的允許大小上限。

    > [!NOTE]
    > 如果輸入的值是 "0"，就會指定記錄檔的大小只受限於可用的磁碟空間。

## <a name="see-also"></a>另請參閱

- [修改負載測試記錄設定](../test/modify-load-test-logging-settings.md)
- [設定測試控制器和測試代理程式的通訊埠](../test/configure-ports-for-test-controllers-and-test-agents.md)