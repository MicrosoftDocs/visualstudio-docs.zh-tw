---
title: CA1000：不要在泛型類型上宣告靜態成員
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1000
- DoNotDeclareStaticMembersOnGenericTypes
helpviewer_keywords:
- DoNotDeclareStaticMembersOnGenericTypes
- CA1000
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f10433330642ee06dd7f705cdd8e35333cd8a79d
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547919"
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000：不要在泛型類型上宣告靜態成員

|||
|-|-|
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|
|CheckId|CA1000|
|Category|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因

泛型型別包含`static` (`Shared`在 Visual Basic) 成員中。

根據預設, 此規則只會查看外部可見的類型, 但這是[可](#configurability)設定的。

## <a name="rule-description"></a>規則描述

呼叫泛型型別的成員時,必須為類型指定類型引數。`static` 呼叫不支援介面的泛型執行個體 (Instance) 成員時，必須為成員指定類型引數。 在這兩種情況下指定類型引數的語法不同且容易混淆, 如下列呼叫所示:

```vb
' Shared method in a generic type.
GenericType(Of Integer).SharedMethod()

' Generic instance method that does not support inference.
someObject.GenericMethod(Of Integer)()
```

```csharp
// Static method in a generic type.
GenericType<int>.StaticMethod();

// Generic instance method that does not support inference.
someObject.GenericMethod<int>();
```

一般來說, 應該避免這兩個先前的宣告, 以便在呼叫成員時不需要指定類型引數。 這會導致在泛型中呼叫成員的語法, 與非泛型的語法不同。 如需詳細資訊, [請參閱 CA1004:泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規, 請移除靜態成員, 或將它變更為實例成員。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。 以易於瞭解和使用的語法提供泛型, 可減少學習及增加新程式庫採用率所需的時間。

## <a name="configurability"></a>可設定性

如果您是從[FxCop 分析器](install-fxcop-analyzers.md)執行此規則 (而不是使用舊版分析), 您可以根據其存取範圍, 設定程式碼基底中的哪些部分來執行此規則。 例如, 若要指定規則只針對非公用 API 介面執行, 請將下列機碼值組新增至專案中的 editorconfig 檔案:

```ini
dotnet_code_quality.ca1000.api_surface = private, internal
```

您可以只針對此規則、所有規則或此類別中的所有規則 (設計) 設定此選項。 如需詳細資訊, 請參閱[設定 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="related-rules"></a>相關規則

- [CA1005避免在泛型型別上有過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010集合應執行泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1002不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006不要在成員簽章中嵌套泛型型別](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003 必須使用一般事件處理常式實例](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007 建議適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>另請參閱

- [泛型](/dotnet/csharp/programming-guide/generics/index)