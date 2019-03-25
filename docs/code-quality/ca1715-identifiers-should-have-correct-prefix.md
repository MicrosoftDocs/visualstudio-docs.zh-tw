---
title: CA1715:識別項名稱應該使用正確的前置字元
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b794eb7c7a258a843763b2c68902000031c17eb3
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57873600"
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715:識別項名稱應該使用正確的前置字元

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|CheckId|CA1715|
|分類|Microsoft.Naming|
|中斷變更|中斷-引發介面上時。<br /><br /> 非分行-時引發的泛型類型參數。|

## <a name="cause"></a>原因

介面名稱以大寫 'I' 不會啟動。

-或-

名稱[泛型型別參數](/dotnet/csharp/programming-guide/generics/generic-type-parameters)型別或方法上不會啟動具有大寫 ' T '。

根據預設，此規則只會查看外部可見介面、 類型和方法，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

依照慣例，具有特定前置詞開頭的特定程式設計項目的名稱。

介面名稱應以大寫字母的 'I' 後面接著另一個大寫字母開頭。 此規則會進行回報介面名稱，例如 'MyInterface' 和 'IsolatedInterface' 的違規。

泛型型別參數名稱應以大寫字母開頭 'T' 和 （選擇性） 後面可能另一個大寫字母。 此規則會進行回報泛型型別參數名稱，例如 'V' 和 'Type' 的違規。

命名慣例提供了通用程式庫 common language runtime 為目標。 這可降低學習曲線，需要新的軟體程式庫，並增加程式庫，開發人員專業開發的 managed 程式碼中的其他人的客戶信心。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定您的程式碼的哪些部分這個規則會分析。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。

### <a name="single-character-type-parameters"></a>單一字元的型別參數

您可以設定要排除此規則的單一字元的型別參數。 例如，若要指定此規則*不應該*分析單一字元的型別參數，請將其中一個的下列索引鍵 / 值組加入至專案中的.editorconfig 檔案：

```
# Package version 2.9.0 and later
dotnet_code_quality.CA1715.exclude_single_letter_type_parameters = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.allow_single_letter_type_parameters = true
```

> [!NOTE]
> 針對名為的型別參數永遠不會觸發此規則`T`，例如`Collection<T>`。

### <a name="api-surface"></a>API 介面

您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```
dotnet_code_quality.ca1715.api_surface = private, internal
```

此類別 （命名） 中，您可以設定此選項，只是這項規則，所有規則，或所有的規則。

## <a name="how-to-fix-violations"></a>如何修正違規

重新命名識別項，以便正確前置詞。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

## <a name="interface-naming-example"></a>介面命名的範例

下列程式碼片段會顯示不正確地命名的介面：

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]

下列程式碼片段會修正上述違規加介面與 'I':

[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]

## <a name="type-parameter-naming-example"></a>型別參數命名範例

下列程式碼片段顯示的命名錯誤的泛型型別參數：

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]

下列程式碼修正上述違規前面加上 ' T 的泛型類型參數 ':

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]

## <a name="related-rules"></a>相關的規則

- [CA1722:識別項不應該有不正確的前置詞](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)