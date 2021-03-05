---
description: 本機電腦 (也就是執行 Visual Studio 的電腦) 上的網際網路連線防火牆，並未設定允許遠端偵錯。
title: 本機電腦上的防火牆 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.firewall.localmachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bad1dcbfa2dd80ade46bd0e848e3c1f186f3c903
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146961"
---
# <a name="error-firewall-on-local-machine"></a>錯誤：本機電腦的防火牆
本機電腦 (也就是執行 Visual Studio 的電腦) 上的網際網路連線防火牆，並未設定允許遠端偵錯。 針對使用預設傳輸的 Managed 或機器碼遠端偵錯，您必須為 DCOM 傳輸開啟 TCP 135 通訊埠。 您必須開啟檔案和印表機共用，並且必須將 devenv.exe 加入例外狀況清單。 可能也必須開啟某些 IPSEC 通訊埠。

 如需詳細資訊，請參閱 [遠端偵錯](../debugger/remote-debugging.md)程式。
