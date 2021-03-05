---
title: 無法連接到電腦 &lt; 名稱 &gt; 。 網路上找不到這部電腦。 | Microsoft Docs
description: 如果下列其中一個條件成立，就會發生此行為： (1) 遠端電腦的連接已中斷。  (2) 遠端電腦上的使用者帳戶已停用。  (3) 您在遠端電腦上的密碼已過期。
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e0d83f043e020ad3c65ac0f986ec174fac95585
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146427"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>錯誤：無法連接到電腦 &lt; 名稱 &gt; 。 網路上找不到這部電腦。
如果下列其中一種情況為 true 時，就會發生這個行為：

- 與遠端電腦的連線中斷。

- 在遠端電腦上的使用者帳戶已停用。

- 遠端電腦上的密碼已到期。

### <a name="to-resolve-this-behavior"></a>若要解決這個行為

- 請確定本機電腦與遠端電腦位於相同的網路上。 方法是，使用 Microsoft Windows [檔案總管] (或 [檔案總管]) 嘗試存取遠端電腦。

     -和-

- 請確定已啟用您用以連接遠端電腦的使用者帳戶。

     -和-

- 請確定您用以連接遠端電腦的密碼是有效的，而且尚未到期。

## <a name="see-also"></a>另請參閱
- [遠端偵錯](../debugger/remote-debugging.md)
- [偵錯工具設定和準備](../debugger/debugger-settings-and-preparation.md)
