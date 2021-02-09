---
title: 設定遠端偵錯程式的防火牆對話方塊 |Microsoft Docs
description: 閱讀 [設定防火牆進行遠端偵錯程式] 對話方塊，這會在 Windows 防火牆停止偵錯工具從網路接收資料時出現。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4fb1d704e2a06ed6c31d6b401b592436c86e4318
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857723"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>設定遠端偵錯防火牆對話方塊
當 Windows 防火牆封鎖偵錯工具，使其無法透過網路接收資訊時，這個對話方塊就會出現。 若要繼續進行遠端偵錯，您必須在防火牆中開啟出入口，讓偵錯工具可以接收資訊。

> [!CAUTION]
> 在防火牆中開啟出入口可能會讓您的電腦暴露在防火牆設計要封鎖的安全性威脅之下。 為遠端偵錯開啟出入口會解除 Visual Studio 2015 中連接埠 4020 和 4021 的封鎖。 在其他 Visual Studio 版本中會使用不同的連接埠號碼。 如需詳細資訊，請參閱 [遠端偵錯程式埠指派](../debugger/remote-debugger-port-assignments.md)。 此外，它還會允許偵錯工具開啟其他通訊埠。 如需詳細資訊，請參閱 [設定 Windows 防火牆以進行遠端偵錯](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。

## <a name="uielement-list"></a>UIElement 清單
 **取消遠端偵錯** 取消遠端偵錯嘗試。 電腦的安全性設定維持不變。

 **從區域網路上的電腦 (子網進行遠端偵錯解除封鎖)** 啟用本機子網上電腦的遠端偵測。 這樣會造成區域子網路上的電腦暴露出弱點，但防火牆會繼續封鎖來自子網路外的資訊。

 **解除封鎖來自任何電腦的遠端偵錯** 可讓您在網路上的任何位置對電腦進行遠端偵錯。 這個設定最不安全。

## <a name="see-also"></a>另請參閱

- [偵錯工具安全性](../debugger/debugger-security.md)
- [遠端偵錯](../debugger/remote-debugging.md)
- [偵錯使用者介面參考](../debugger/debugging-user-interface-reference.md)