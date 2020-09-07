---
title: 可攜性和互通性警告
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings, portability warnings
- portability warnings
- warnings, portability
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 306c2477e6e5f731ed6dbf20b2cf4d03d4556467
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509909"
---
# <a name="portability-and-interoperability-warnings"></a>可攜性和互通性警告

可攜性警告支援跨不同平臺的可攜性。 互通性警告支援與 COM 用戶端互動。

## <a name="in-this-section"></a>本節內容

| 規則 | 描述 |
| - | - |
| [CA1401： P/Invoke 不應該為可見的](../code-quality/ca1401.md) | 公用類型中的公用或受保護方法具有 System.Runtime.InteropServices.Dll的 ImportAttribute 屬性 (也會由 Visual Basic) 中的 Declare 關鍵字來執行。 但不得公開 (Expose) 此類方法。 |
| [CA1417：不使用 `OutAttribute` P/invoke 的字串參數](../code-quality/ca1417.md) | 以傳值方式傳遞的字串參數， `OutAttribute` 會在字串為暫存字串時，使執行時間不穩定。 |