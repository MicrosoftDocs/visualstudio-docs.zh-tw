---
title: CA2226:運算子應該有對稱的多載
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4557b61afab08c7db05c734c6f2ac927a40edb71
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69546860"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226:運算子應該有對稱的多載

|||
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|Category|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因

類型實作等號比較運算子或不等比較運算子，但未實作相反的運算子。

根據預設, 此規則只會查看外部可見的類型, 但這是[可](#configurability)設定的。

## <a name="rule-description"></a>規則描述

在某些情況下, 不相等或不等比較適用于類型的實例, 而且相反的運算子未定義。 類型通常會藉由傳回等號比較運算子的負值來實作為不等運算子。

C#編譯器會發出錯誤, 以違反此規則。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規, 請同時執行相等和不等比較運算子, 或移除存在的運算子。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。 如果您這樣做, 您的型別將無法以與 .NET 一致的方式來使用。

## <a name="configurability"></a>可設定性

如果您是從[FxCop 分析器](install-fxcop-analyzers.md)執行此規則 (而不是使用舊版分析), 您可以根據其存取範圍, 設定程式碼基底中的哪些部分來執行此規則。 例如, 若要指定規則只針對非公用 API 介面執行, 請將下列機碼值組新增至專案中的 editorconfig 檔案:

```ini
dotnet_code_quality.ca2226.api_surface = private, internal
```

您可以只針對此規則、所有規則或此類別中的所有規則 (使用方式) 設定此選項。 如需詳細資訊, 請參閱[設定 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="related-rules"></a>相關規則

- [CA1046不要多載參考型別上的運算子 equals](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2225運算子多載具有已命名的替代項](../code-quality/ca2225-operator-overloads-have-named-alternates.md)
- [CA2224多載運算子 equals 的覆寫 equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218覆寫覆寫 Equals 上的 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231：在覆寫 ValueType.Equals 上多載等號運算子](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)