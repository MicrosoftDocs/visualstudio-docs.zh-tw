---
title: 錯誤：無法起始 DCOM 通訊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unmarshal_server_failed
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
ms.openlocfilehash: 8a5e45df06d4b9490160c94902457ea630548966
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736720"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>錯誤：無法啟始 DCOM 通訊
當本機電腦 (Local Machine) 嘗試與遠端機器進行通訊時，就會發生 DCOM 錯誤。 這個錯誤發生的原因，是因為遠端伺服器上的防火牆，或是遠端機器上的 Windows 驗證中斷所造成。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 如果遠端電腦已啟用 Windows 防火牆，請參閱[遠端偵錯](../debugger/remote-debugging.md)程式，以取得有關如何設定防火牆以進行本機偵測的指示。

- 若要還原 Windows 驗證，請嘗試重新啟動本機電腦和遠端電腦。 在本機和遠端機器上檢查 Kerberos 錯誤的事件日誌，並連絡網域系統管理員以瞭解已知的問題。

## <a name="see-also"></a>請參閱
- [Remote Debugging](../debugger/remote-debugging.md)