---
title: CA1402：避免在 COM 可見介面中多載
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1617ad2d5132f22da3c25565e6310977b286eaef
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444333"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402：避免在 COM 可見介面中多載

|||
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|分類|Microsoft. 互通性|
|重大變更|中斷|

## <a name="cause"></a>原因
元件物件模型（COM）可見介面會宣告多載的方法。

## <a name="rule-description"></a>規則描述
當多載方法會對 COM 用戶端公開 (Expose) 時，只有第一個方法多載會保留它的名稱。 後續的多載會藉由附加至名稱加上底線字元 ' _ '，以及對應至多載宣告順序的整數來進行唯一重新命名。 例如，請考慮下列方法：

```csharp
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

這些方法會公開給 COM 用戶端，如下所示。

```csharp
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

Visual Basic 6 COM 用戶端無法使用名稱中的底線來執行介面方法。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形，請重新命名多載的方法，讓名稱成為唯一的。 或者，藉由將存取範圍變更為 `internal` （在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中 `Friend`），或將 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 屬性設定為 `false`，讓 COM 無法看到介面。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
下列範例顯示違反規則的介面，以及符合規則的介面。

[!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
[!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]

## <a name="related-rules"></a>相關規則
[CA1413：避免在 COM 可見實值型別中使用非公用欄位](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

[CA1407：避免在 COM 可見類型中使用靜態成員](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017：組件必須標記 ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>請參閱

- [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)
- [Long 資料類型](/dotnet/visual-basic/language-reference/data-types/long-data-type)
