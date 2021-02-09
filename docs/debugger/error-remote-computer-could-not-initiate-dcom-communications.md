---
title: 遠端電腦無法起始 DCOM 通訊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
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
ms.openlocfilehash: ecc23af6335aa29adcad6dbe9e7869ab26cc0bc6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871477"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>錯誤：遠端電腦無法啟始 DCOM 通訊
當遠端電腦嘗試與本機電腦進行通訊時，就會發生 DCOM 錯誤。 本機電腦是

 執行 Visual Studio 的電腦。 發生這個錯誤的原因有下列幾種︰

- 本機電腦啟用了防火牆。

- 從遠端電腦到本機電腦的 Windows 驗證尚未運作。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 如果本機電腦已啟用 Windows 防火牆，請參閱 [遠端偵錯](../debugger/remote-debugging.md) 程式，以取得如何設定防火牆進行本機調試的指示。

2. 測試 Windows 驗證，方法是嘗試從遠端伺服器上開啟本機電腦上的共用檔案。

3. 若要還原 Windows 驗證，請嘗試重新啟動本機電腦和遠端電腦。 在本機和遠端機器上檢查 Kerberos 錯誤的事件日誌，並連絡網域系統管理員以瞭解已知的問題。

## <a name="see-also"></a>另請參閱
 [遠端偵錯](../debugger/remote-debugging.md)