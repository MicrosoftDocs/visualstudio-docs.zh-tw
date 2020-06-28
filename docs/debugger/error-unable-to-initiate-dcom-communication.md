---
title: 錯誤-無法起始 DCOM 通訊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: ccd8b30fcba11d89e11227861c4582ff67f3a7e7
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460022"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>錯誤：無法啟始 DCOM 通訊
當本機電腦 (Local Machine) 嘗試與遠端機器進行通訊時，就會發生 DCOM 錯誤。 這個錯誤發生的原因，是因為遠端伺服器上的防火牆，或是遠端機器上的 Windows 驗證中斷所造成。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 如果遠端電腦已啟用 Windows 防火牆，請參閱[遠端偵錯](../debugger/remote-debugging.md)程式，以取得有關如何設定防火牆以進行本機偵測的指示。

- 若要還原 Windows 驗證，請嘗試重新啟動本機電腦和遠端電腦。 在本機和遠端機器上檢查 Kerberos 錯誤的事件日誌，並連絡網域系統管理員以瞭解已知的問題。

## <a name="see-also"></a>另請參閱
- [遠端偵錯](../debugger/remote-debugging.md)