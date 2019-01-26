---
title: CA1000：不要在泛型類型上宣告靜態成員
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: f15fc2bf7a8bc4e7e47efaad351ac33638195afd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971750"
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000：不要在泛型類型上宣告靜態成員

|||
|-|-|
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|
|CheckId|CA1000|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見的泛型型別包含`static`(`Shared` Visual Basic 中) 成員。

## <a name="rule-description"></a>規則描述
 當`static`泛型型別的成員呼叫、 型別引數必須指定的類型。 呼叫不支援介面的泛型執行個體 (Instance) 成員時，必須為成員指定類型引數。 在這兩種案例中指定的型別引數的語法是不同且容易混淆，示範下列呼叫：

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

 一般而言，這兩個先前宣告應避免，因此不需要呼叫成員時指定的型別引數。 這會導致語法中的泛型與非泛型的語法並無不同，呼叫的成員。 如需詳細資訊，請參閱[CA1004:泛型方法應該提供型別參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除靜態成員，或將它變更為執行個體成員。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 提供了容易了解和使用的語法中的泛型減少時間，才能了解，並增加新的程式庫的採用率。

## <a name="related-rules"></a>相關的規則
 [CA1005:避免在泛型類型上的過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010:集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1002:不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006:無法建立巢狀成員簽章中的泛型型別](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004:泛型方法應該提供型別參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003： 必須使用一般事件處理常式執行個體](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007:在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>另請參閱
 [泛型](/dotnet/csharp/programming-guide/generics/index)