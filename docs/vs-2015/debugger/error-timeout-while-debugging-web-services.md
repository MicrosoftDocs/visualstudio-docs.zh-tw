---
title: 錯誤：偵錯 Web 服務時的逾時 |Microsoft Docs
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
ms.openlocfilehash: 5745a23e70f9245d6f1cb34a6d4ccc042f64bdd3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538326"
---
# <a name="error-timeout-while-debugging-web-services"></a>錯誤：對 Web 服務進行偵錯時逾時
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

## <a name="see-also"></a>另請參閱
- [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
