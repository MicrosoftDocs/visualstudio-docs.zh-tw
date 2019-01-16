---
title: 錯誤：在本機電腦上的防火牆 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.firewall.localmachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d2fafd14a816f75ac4acdf4de7db0ceda1430652
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53919835"
---
# <a name="error-firewall-on-local-machine"></a>錯誤：本機電腦的防火牆
本機電腦 (也就是執行 Visual Studio 的電腦) 上的網際網路連線防火牆，並未設定允許遠端偵錯。 針對使用預設傳輸的 Managed 或機器碼遠端偵錯，您必須為 DCOM 傳輸開啟 TCP 135 通訊埠。 您必須開啟檔案和印表機共用，並且必須將 devenv.exe 加入例外狀況清單。 可能也必須開啟某些 IPSEC 通訊埠。  
  
 如需詳細資訊，請參閱 <<c0> [ 遠端偵錯](../debugger/remote-debugging.md)。