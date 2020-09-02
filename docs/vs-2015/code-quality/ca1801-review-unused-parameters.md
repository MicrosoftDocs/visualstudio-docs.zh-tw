---
title: CA1801 必須：檢查未使用的參數 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c87836f99684c7e16c022e3e9f15bf546ba82d62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547780"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801:必須檢閱未使用的參數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 的最新檔，請參閱 [ca1801 必須：複習未使用的參數](/visualstudio/code-quality/ca1801-review-unused-parameters)。

|Item|值|
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|類別|Microsoft. 使用量|
|中斷變更|不中斷-如果在元件外部看不到成員，則不論您所做的變更為何。<br /><br /> 非中斷-如果您變更成員以在其主體內使用參數。<br /><br /> 中斷-如果您移除參數，它在元件外部是可見的。|

## <a name="cause"></a>原因
 方法簽章包括不用於方法主體中的參數； 此規則不會檢查下列方法：

- 委派所參考的方法。

- 當做事件處理常式使用的方法。

- 使用 `abstract` Visual Basic) 修飾詞中的 (宣告的方法 `MustOverride` 。

- 使用 `virtual` Visual Basic) 修飾詞中的 (宣告的方法 `Overridable` 。

- 使用 `override` Visual Basic) 修飾詞中的 (宣告的方法 `Overrides` 。

- 使用 `extern` Visual Basic) 修飾詞中的 (語句宣告的方法 `Declare` 。

## <a name="rule-description"></a>規則描述
 請參閱未在方法主體中使用之非虛擬方法中的參數，以確保無法存取它們的正確性。 未使用的參數會產生維護和效能成本。

 有時違反此規則可能會指向方法中的實 bug。 例如，參數應該已用於方法主體中。 如果因為回溯相容性而必須存在參數，則隱藏此規則的警告。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除未使用的參數 (中斷變更) 或在方法主體中使用參數 (非中斷變更) 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 您可以安全地隱藏此規則中的警告，以供修正程式中斷變更的先前發行程式碼使用。

## <a name="example"></a>範例
 下列範例顯示兩個方法。 其中一個方法違反規則，另一個方法則符合規則。

 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ReviewUnusedParameters/cs/FxCop.Usage.ReviewUnusedPerameters.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA1811:避免使用未呼叫的私用程式碼](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812:避免使用未執行個體化的內部類別](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804:必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)
