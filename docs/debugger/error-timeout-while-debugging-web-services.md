---
title: 錯誤：調試 Web 服務時發生超時 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5aba4fef3e1c787651eb961f80b3507090f250a2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736882"
---
# <a name="error-timeout-while-debugging-web-services"></a>錯誤：偵錯 Web 服務時逾時
當您從呼叫程式碼逐步執行 XML Web Service 時，呼叫有時可能會逾時，並產生無法繼續偵錯的結果。 您可能會看到像這樣的錯誤訊息。

```cmd
An unhandled exception of type 'System.Net.WebException' occurred in
system.Web.services.dll
Additional information: The operation has timed-out.
```

## <a name="solution"></a>方案
 為避免發生這個問題，請將 XML Web Service 呼叫的逾時值設成無限，如這個範例中所示：

```csharp
Service1 obj = new Service1();
obj.TimeOut = -1; // infinite time out.
```

## <a name="see-also"></a>請參閱
- [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
