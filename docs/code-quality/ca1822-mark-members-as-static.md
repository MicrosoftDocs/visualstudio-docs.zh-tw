---
title: CA1822:將成員標記為 static
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f25b74949c734921c313ae2cf00a2d217029e52
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921378"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822:將成員標記為 static

|||
|-|-|
|TypeName|MarkMembersAsStatic|
|CheckId|CA1822|
|分類|Microsoft.Performance|
|中斷變更|不中斷-如果在元件外部看不到成員, 不論您所做的變更為何。 不中斷-如果您只使用`this`關鍵字將成員變更為實例成員。<br /><br /> 中斷-如果您將成員從實例成員變更為靜態成員, 而且它在元件外部是可見的。|

## <a name="cause"></a>原因
未存取實例資料的成員未標記為靜態 (在中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]為 Shared)。

## <a name="rule-description"></a>規則描述
不會存取執行個體資料或不會呼叫執行個體方法的成員，可以標記為 static (在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中為 Shared)。 將方法標記為 static 之後，編譯器將對這些成員發出非虛擬呼叫位置。 發出非虛擬的呼叫位置, 將可防止每個呼叫的執行時間檢查, 以確保目前的物件指標為非 null。 這麼做可讓效能敏感的程式碼獲得顯著的效能提升。 在某些情況下, 存取目前物件實例的失敗表示正確性的問題。

## <a name="how-to-fix-violations"></a>如何修正違規
將成員標記為靜態 (或在中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]為 Shared), 或在方法主體中使用 ' this '/' Me ' (如果適用的話)。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
針對先前出貨的程式碼, 您可以放心地隱藏此規則中的警告, 這是一項重大變更。

## <a name="related-rules"></a>相關規則
[CA1811避免使用未呼叫的私用程式碼](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812避免未具現化的內部類別](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1804 必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)