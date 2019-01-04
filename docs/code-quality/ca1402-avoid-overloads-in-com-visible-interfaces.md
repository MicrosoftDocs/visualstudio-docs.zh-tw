---
title: CA1402:避免在 COM 可見介面中多載
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 056e572ef7a572c83731851d49420e0c713c6cc9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53935524"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402:避免在 COM 可見介面中多載

|||
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|類別|Microsoft.Interoperability|
|中斷變更|中斷|

## <a name="cause"></a>原因
 元件物件模型 (COM) 可見的介面會宣告多載方法。

## <a name="rule-description"></a>規則描述
 當多載方法會對 COM 用戶端公開 (Expose) 時，只有第一個方法多載會保留它的名稱。 後續的多載會重新命名為唯一的名稱附加底線字元 '_' 和對應的多載的宣告順序的整數來。 例如，請考慮下列方法：

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

Visual Basic 6 COM 用戶端無法實作介面方法，名稱中使用底線。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，多載的方法重新命名，名稱是唯一的。 或者，使介面看不到 COM 藉由變更以協助工具`internal`(`Friend`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 或藉由套用<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>屬性設為`false`。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的介面和介面，會滿足規則。

 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]

## <a name="related-rules"></a>相關的規則
 [CA1413:避免在 COM 可見實值類型中的非公用欄位](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407:避免在 COM 可見類型中的靜態成員](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017:組件必須標記 comvisibleattribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>另請參閱

- [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)
- [Long 資料類型](/dotnet/visual-basic/language-reference/data-types/long-data-type)