---
title: CA1407： 避免在 COM 可見類型中的靜態成員 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9b3d14351ddb0e7e98c5c93bd1fe62c5b106dca1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889044"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407：避免在 COM 可見類型中使用靜態成員
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersViolation/cs/FxCop.Interoperability.ComVisibleStaticMembersViolation.cs#1)]

### <a name="comments"></a>註解
 在此範例中， **Book.FromPages**方法無法從 COM 呼叫

## <a name="example-fix"></a>範例的修正程式

### <a name="description"></a>描述
 若要修正此違規情形在上述範例中，您可以將方法變更為執行個體方法，但是，不合理這個執行個體中。 更好的解決方案是明確地套用`ComVisible(false)`至方法，以讓它清除方法，無法從 COM 中看到其他開發人員

 下列範例會套用<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>方法。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersFixed/cs/FxCop.Interoperability.ComVisibleStaticMembersFixed.cs#1)]

## <a name="related-rules"></a>相關的規則
 [CA1017：組件必須標記 ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406：避免對 Visual Basic 6 用戶端使用 Int64 引數](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413：避免在 COM 可見實值型別中使用非公用欄位](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>另請參閱
 [與 Unmanaged 程式碼互通](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



