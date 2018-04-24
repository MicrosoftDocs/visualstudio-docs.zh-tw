---
title: CA1051：不要宣告可見的執行個體欄位
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb322ffb6f3603001e9fa673eb9daf9f28d73b18
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051：不要宣告可見的執行個體欄位
|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見的類型有外部可見的執行個體欄位。

## <a name="rule-description"></a>規則描述
 欄位的主要用法應該是當做實作詳細資料。 欄位應該具備`private`或`internal`，而且應使用屬性公開。 很容易存取的屬性，它是存取欄位，以及展開而不會引進重大變更的類型的功能可以變更的屬性存取子中的程式碼。 只傳回私用或內部欄位的值的屬性已最佳化，以執行與同等存取欄位。很少的效能提升是使用外部可見欄位相關聯的屬性上。

 外部可見的指`public`， `protected`，和`protected internal`(`Public`， `Protected`，和`Protected Friend`在 Visual Basic) 存取範圍層級。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將欄位設定`private`或`internal`並將它公開使用的外部可見的屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 外部可見的欄位不會提供屬性沒有任何優點。 此外，公用欄位無法由保護[連結要求](/dotnet/framework/misc/link-demands)。 請參閱[CA2112： 受保護的類型不應該公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)。

## <a name="example"></a>範例
 下列範例顯示型別 (`BadPublicInstanceFields`) 違反此規則。 `GoodPublicInstanceFields` 顯示更正的程式碼。

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>相關的規則
 [CA2112：受保護類型不應該公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>另請參閱
 [連結要求](/dotnet/framework/misc/link-demands)