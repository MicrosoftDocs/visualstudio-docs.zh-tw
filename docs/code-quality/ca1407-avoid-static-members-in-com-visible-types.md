---
title: CA1407:避免在 COM 可見類型中使用靜態成員
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f72949326cf52455013c20419202b358b06d8b0b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916435"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407:避免在 COM 可見類型中使用靜態成員

|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|分類|Microsoft.Interoperability|
|中斷變更|非重大|

## <a name="cause"></a>原因
 特別標示為可見的元件物件模型 (COM) 的型別含有`public``static`方法。

## <a name="rule-description"></a>規則描述
 COM 不支援`static`方法。

 此規則會忽略屬性和事件存取子、 運算子多載方法或使用其中一種標記的方法可<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>屬性或<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>屬性。

 根據預設，以下是為 COM 所見： 組件、 公用型別、 公用的型別中的公用執行個體成員和公用實值型別的所有成員。

 此規則，若要進行的組件層級<xref:System.Runtime.InteropServices.ComVisibleAttribute>必須設為`false`和 [類別]-<xref:System.Runtime.InteropServices.ComVisibleAttribute>必須設為`true`，如下列程式碼所示。

```csharp
using System;
using System.Runtime.InteropServices;

[assembly: ComVisible(false)]
namespace Samples
{
    [ComVisible(true)]
    public class MyClass
    {
        public static void DoSomething()
        {
        }
    }
}
```

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，變更 使用執行個體的方法，提供相同的功能設計`static`方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏此規則的警告，如果 COM 用戶端不需要存取所提供的功能`static`方法。

## <a name="example-violation"></a>範例違規

### <a name="description"></a>描述
 下列範例所示`static`違反此規則的方法。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]

### <a name="comments"></a>註解
 在此範例中， **Book.FromPages**方法無法從 COM 呼叫

## <a name="example-fix"></a>範例的修正程式

### <a name="description"></a>描述
 若要修正此違規情形在上述範例中，您可以將方法變更為執行個體方法，但是，不合理這個執行個體中。 更好的解決方案是明確地套用`ComVisible(false)`至方法，以讓它清除方法，無法從 COM 中看到其他開發人員

 下列範例會套用<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>方法。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]

## <a name="related-rules"></a>相關的規則
 [CA1017:組件必須標記 comvisibleattribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406:避免對 Visual Basic 6 用戶端的 Int64 引數](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413:避免在 COM 可見實值類型中的非公用欄位](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>另請參閱
 [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)