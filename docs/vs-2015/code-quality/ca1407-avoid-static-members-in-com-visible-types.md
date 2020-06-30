---
title: CA1407：避免在 COM 可見類型中的靜態成員 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 436a8614c18c296c072d91116143306d898f0436
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538849"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407:避免在 COM 可見類型中使用靜態成員
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|類別|Microsoft. 互通性|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 特別標示為「元件物件模型（COM）可見」的類型包含 `public``static` 方法。

## <a name="rule-description"></a>規則描述
 COM 不支援 `static` 方法。

 此規則會忽略屬性和事件存取子、運算子多載方法，或使用 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 屬性或屬性標記的方法 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 。

 根據預設，COM 會看到下列內容：元件、公用類型、公用類型中的公用實例成員，以及公用實數值型別的所有成員。

 若要讓此規則發生，元件層級 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 必須設定為， `false` 且類別 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 必須設定為 `true` ，如下列程式碼所示。

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
 若要修正此規則的違規情形，請將設計變更為使用提供與方法相同功能的實例方法 `static` 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果 COM 用戶端不需要存取方法所提供的功能，就可以放心地隱藏此規則的警告 `static` 。

## <a name="example-violation"></a>範例違規

### <a name="description"></a>描述
 下列範例顯示 `static` 違反此規則的方法。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersViolation/cs/FxCop.Interoperability.ComVisibleStaticMembersViolation.cs#1)]

### <a name="comments"></a>註解
 在此範例中，無法從 COM 呼叫**FromPages**方法。

## <a name="example-fix"></a>範例修正

### <a name="description"></a>描述
 若要修正上述範例中的違規，您可以將方法變更為實例方法，但這在此實例中沒有意義。 更好的解決方案是明確地套用 `ComVisible(false)` 至方法，讓其他開發人員清楚知道方法無法從 COM 看到。

 下列範例適用于 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> 方法。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersFixed/cs/FxCop.Interoperability.ComVisibleStaticMembersFixed.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA1017:組件必須標記 ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406:避免對 Visual Basic 6 用戶端使用 int64 引數](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413:避免在 COM 可見實值類型中使用非公用欄位](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>另請參閱
 [與 Unmanaged 程式碼互通](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
