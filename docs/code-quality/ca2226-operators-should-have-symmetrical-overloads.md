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
ms.openlocfilehash: a903fbd3b01523a86302b58f8e9a74917312566c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541727"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226:運算子應該有對稱的多載

|||
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因

類型實作等號比較運算子或不等比較運算子，但未實作相反的運算子。

根據預設，此規則只會查看外部可見的類型，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

沒有其中相等或不等比較是適用於類型的執行個體，而相反的運算子是未定義的情況。 通常，型別會實作不等比較運算子所傳回的等號比較運算子的相反的值。

C# 編譯器會發出這項規則的違規錯誤。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，實作相等和不等比較運算子，或移除的存在。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。 如果您這樣做，您的型別不適用於以.NET 與一致的方式。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```
dotnet_code_quality.ca2226.api_surface = private, internal
```

您可以設定此選項只是這項規則，所有規則，或所有規則 （使用） 這個類別中。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="related-rules"></a>相關的規則

- [CA1046:不要多載參考類型上的等號比較運算子](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2225:運算子多載必須有具名的替代項目](../code-quality/ca2225-operator-overloads-have-named-alternates.md)
- [CA2224:覆寫等於多載等號比較運算子](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218:Equals 覆寫 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231：在覆寫 ValueType.Equals 上多載等號運算子](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)