---
title: 錯誤：遠端電腦無法啟始 DCOM 通訊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ceb796b3a4b3cbc2b239a09ac8c173e746f194c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091196"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>錯誤：遠端電腦無法起始 DCOM 通訊
當遠端電腦嘗試與本機電腦進行通訊時，就會發生 DCOM 錯誤。 本機電腦是

 執行 Visual Studio 的電腦。 發生這個錯誤的原因有下列幾種︰

- 本機電腦啟用了防火牆。

- 從遠端電腦到本機電腦的 Windows 驗證尚未運作。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 如果本機電腦已啟用的 Windows 防火牆，請參閱[遠端偵錯](../debugger/remote-debugging.md)如需有關如何設定防火牆以供進行本機偵錯的指示。

2. 測試 Windows 驗證，方法是嘗試從遠端伺服器上開啟本機電腦上的共用檔案。

3. 若要還原 Windows 驗證，請嘗試重新啟動本機電腦和遠端電腦。 在本機和遠端機器上檢查 Kerberos 錯誤的事件日誌，並連絡網域系統管理員以瞭解已知的問題。

## <a name="see-also"></a>另請參閱
 [Remote Debugging](../debugger/remote-debugging.md)