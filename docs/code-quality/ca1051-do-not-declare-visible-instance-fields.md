---
title: CA1051:不要宣告可見的執行個體欄位
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56e5c8f0a0e703bfa2a2cc2419d1bd3be0b0f23a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917221"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051:不要宣告可見的執行個體欄位

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見的類型都有的外部可見的執行個體欄位。

## <a name="rule-description"></a>規則描述
 欄位的主要用法應該是當做實作詳細資料。 欄位應該`private`或`internal`，而且應該使用屬性公開。 很容易存取的屬性，它可存取的欄位，以及可以變更的屬性存取子中的程式碼，如型別的功能展開，而不導入重大變更。 只會傳回私用或內部欄位的值的屬性已最佳化，以執行與同等存取欄位;很少效能已改善使用外部可見欄位相關聯屬性。

 外部可見的指`public`， `protected`，並`protected internal`(`Public`， `Protected`，和`Protected Friend`Visual Basic 中) 存取範圍層級。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將欄位設`private`或`internal`並將它公開使用的外部可見的屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 外部可見的欄位不會提供屬性無法使用的任何權益。 此外，公用欄位不能受到[連結要求](/dotnet/framework/misc/link-demands)。 請參閱[CA2112:受保護的類型不應該公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)。

## <a name="example"></a>範例
 下列範例顯示型別 (`BadPublicInstanceFields`)，違反這項規則。 `GoodPublicInstanceFields` 顯示更正的程式碼。

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>相關的規則
 [CA2112:受保護的類型不應該公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>另請參閱
 [連結要求](/dotnet/framework/misc/link-demands)