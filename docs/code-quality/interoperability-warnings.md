---
title: 可攜性和互通性警告
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis rules, interoperability rules, portability rules
- portability rules
- rules, portability
- interoperability rules
- rules, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8a456f4a24339b6cba5aeec2c9fe64ad3ee278b
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808596"
---
# <a name="portability-and-interoperability-rules"></a>可攜性和互通性規則

可攜性規則支援跨不同平臺的可攜性。 互通性規則支援與 COM 用戶端互動。

## <a name="in-this-section"></a>本節內容

| 規則 | 描述 |
| - | - |
| [CA1401： P/Invoke 不應該為可見的](../code-quality/ca1401.md) | 公用類型中的公用或受保護方法具有 System.Runtime.InteropServices.Dll的 ImportAttribute 屬性 (也會由 Visual Basic) 中的 Declare 關鍵字來執行。 但不得公開 (Expose) 此類方法。 |
| [CA1416：驗證平台相容性](../code-quality/ca1416.md) | 在元件上使用平臺相依的 Api，可讓程式碼無法在所有平臺上運作。 |
| [CA1417：不使用 `OutAttribute` P/invoke 的字串參數](../code-quality/ca1417.md) | 以傳值方式傳遞的字串參數， `OutAttribute` 會在字串為暫存字串時，使執行時間不穩定。 |
