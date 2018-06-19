---
title: '錯誤: 本機電腦上防火牆 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: e85c97d5950f71d9552bba944450603e47a5ab49
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472863"
---
# <a name="error-firewall-on-local-machine"></a>錯誤：本機電腦的防火牆
本機電腦 (也就是執行 Visual Studio 的電腦) 上的網際網路連線防火牆，並未設定允許遠端偵錯。 針對使用預設傳輸的 Managed 或機器碼遠端偵錯，您必須為 DCOM 傳輸開啟 TCP 135 通訊埠。 您必須開啟檔案和印表機共用，並且必須將 devenv.exe 加入例外狀況清單。 可能也必須開啟某些 IPSEC 通訊埠。  
  
 如需詳細資訊，請參閱[遠端偵錯](../debugger/remote-debugging.md)。