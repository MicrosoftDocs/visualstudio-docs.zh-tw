---
title: CA1801:必須檢閱未使用的參數
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee9500938feb893627069e9a83f3052fa84bc224
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545507"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801:必須檢閱未使用的參數

|||
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|分類|Microsoft.Usage|
|中斷變更|非中斷-成員不是組件，不論您所做的變更外部可見。<br /><br /> 非中斷-如果您變更要使用的參數，其主體中的成員。<br /><br /> 中斷-如果您移除參數，而且它是組件外部可見。|

## <a name="cause"></a>原因
 方法簽章包括不用於方法主體中的參數； 此規則不會檢查下列方法：

- 委派所參考的方法。

- 做為事件處理常式的方法。

- 方法宣告`abstract`(`MustOverride` Visual Basic 中) 修飾詞。

- 方法宣告`virtual`(`Overridable` Visual Basic 中) 修飾詞。

- 方法宣告`override`(`Overrides` Visual Basic 中) 修飾詞。

- 方法宣告`extern`(`Declare` Visual Basic 中的陳述式) 修飾詞。

## <a name="rule-description"></a>規則描述
 檢閱中不會在方法主體中以確定解決無法存取它們的不正確性存在的非虛擬方法的參數。 未使用的參數會產生維護與效能的費用。

 有時候這項規則的違規情形可以指向方法中實作錯誤。 例如，參數應該已經用於方法主體。 如果參數對因回溯相容性而存在，則隱藏此規則的警告。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，移除未使用的參數 （重大變更），或使用參數在方法主體中 （非中斷變更）。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏此規則，先前隨附的程式碼修正會是一項重大變更的警告。

## <a name="example"></a>範例
 下列範例顯示兩個方法。 其中一種方法違反此規則，另一種方法會滿足規則。

 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]

## <a name="related-rules"></a>相關的規則
 [CA1811:避免使用未呼叫的私用程式碼](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812:避免使用未執行個體化的內部類別](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804： 必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)