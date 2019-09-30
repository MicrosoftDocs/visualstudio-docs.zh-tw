---
title: CA1801:必須檢閱未使用的參數
ms.date: 06/24/2019
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
ms.openlocfilehash: 6de48bf273a5c93afcd14e7bab2c5d4c4c4b5a7c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233831"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801:必須檢閱未使用的參數

|||
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|分類|Microsoft.Usage|
|重大變更|不中斷-如果在元件外部看不到成員，不論您所做的變更為何。<br /><br /> 不中斷-如果您變更成員，以在其主體內使用參數。<br /><br /> 中斷-如果您移除參數，而且它在元件外部是可見的。|

## <a name="cause"></a>原因

方法簽章包含未在方法主體中使用的參數。

此規則不會檢查下列種類的方法：

- 委派所參考的方法。

- 當做事件處理常式使用的方法。

- 以`abstract` （`MustOverride` Visual Basic）修飾詞宣告的方法。

- 以`virtual` （`Overridable` Visual Basic）修飾詞宣告的方法。

- 以`override` （`Overrides` Visual Basic）修飾詞宣告的方法。

- 使用（ `extern` `Declare` Visual Basic 中的語句）修飾詞宣告的方法。

如果您使用[FxCop 分析器](install-fxcop-analyzers.md)，此規則不會標示以[捨棄](/dotnet/csharp/discards)符號命名的參數`_`， `_1`例如、和`_2`。 這可減少簽章需求所需參數的警告雜訊，例如，當做委派使用的方法、具有特殊屬性的參數，或在執行時間由架構隱含存取其值，但未在中參考的參數錯誤碼.

## <a name="rule-description"></a>規則描述

請參閱未在方法主體中使用之非虛擬方法中的參數，以確保在存取失敗時不會有 incorrectness 存在。 未使用的參數會產生維護和效能成本。

有時候，違反此規則可能會指向方法中的實作為 bug。 例如，參數應該已用於方法主體中。 如果參數因為回溯相容性而必須存在，請隱藏此規則的警告。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規，請移除未使用的參數（中斷變更），或在方法主體中使用參數（非中斷變更）。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

您可以放心地隱藏此規則中的警告：

- 在先前隨附的程式碼中，修正會是中斷性變更。

- 適用于`this`自訂擴充<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=nameWithType>方法中的參數。 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>類別中的函式是靜態的，因此不需要存取方法主體中`this`的參數。

## <a name="example"></a>範例

下列範例顯示兩個方法。 其中一個方法違反規則，另一個方法則符合規則。

[!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]

## <a name="related-rules"></a>相關規則

[CA1811避免使用未呼叫的私用程式碼](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812避免未具現化的內部類別](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1804 必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)
