---
title: CA1407：避免在 COM 可見類型中使用靜態成員
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: f14e3b2577d182db432402a267e8bd6979736186
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407：避免在 COM 可見類型中使用靜態成員
|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|分類|Microsoft.Interoperability|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 包含特別標示為可見元件物件模型 (COM) 的類型`public``static`方法。

## <a name="rule-description"></a>規則描述
 COM 不支援`static`方法。

 此規則會忽略屬性和事件存取子、 運算子多載方法或使用標記的方法可<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>屬性或<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>屬性。

 根據預設，以下是為 COM 可見： 組件、 公用型別、 公用的型別中的公用執行個體成員和公用實值型別的所有成員。

 此規則，若要進行的組件層級<xref:System.Runtime.InteropServices.ComVisibleAttribute>必須設為`false`和類別-<xref:System.Runtime.InteropServices.ComVisibleAttribute>必須設為`true`，如下列程式碼所示。

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
 若要修正此規則的違規情形，變更要使用提供的相同功能與執行個體方法設計`static`方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 安全地隱藏此規則的警告，如果 COM 用戶端不需要存取所提供的功能`static`方法。

## <a name="example-violation"></a>範例違規

### <a name="description"></a>描述
 下列範例所示`static`違反此規則的方法。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]

### <a name="comments"></a>註解
 在此範例中， **Book.FromPages**方法不能從 COM 呼叫

## <a name="example-fix"></a>修正範例

### <a name="description"></a>描述
 若要修正上述範例中的違規，您無法將方法變更為執行個體方法，但是，不具意義這個執行個體中。 更好的解決方案是明確地套用`ComVisible(false)`清除給其他開發人員方法看從 COM 方法

 下列範例會套用<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>方法。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]

## <a name="related-rules"></a>相關的規則
 [CA1017：組件必須標記 ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406：避免對 Visual Basic 6 用戶端使用 Int64 引數](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413：避免在 COM 可見實值型別中使用非公用欄位](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>另請參閱
 [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)