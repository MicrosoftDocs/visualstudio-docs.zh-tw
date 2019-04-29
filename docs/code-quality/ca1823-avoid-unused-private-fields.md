---
title: CA1823:避免包含未使用的私用欄位
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68d7f521927497a50779d77c4d7bdd8520ac222f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545250"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823:避免包含未使用的私用欄位

|||
|-|-|
|TypeName|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|分類|Microsoft.Performance|
|中斷變更|非重大|

## <a name="cause"></a>原因
 此規則會報告當您的程式碼中的私用欄位存在，但不是會使用任何程式碼路徑。

## <a name="rule-description"></a>規則描述
 偵測到似乎不能在組件內存取的私用欄位。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，移除欄位，或加入程式碼使用它。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏此規則的警告。

## <a name="related-rules"></a>相關的規則
 [CA1812:避免使用未執行個體化的內部類別](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801： 必須檢閱未使用的參數](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804： 必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)

 [CA1811:避免使用未呼叫的私用程式碼](../code-quality/ca1811-avoid-uncalled-private-code.md)