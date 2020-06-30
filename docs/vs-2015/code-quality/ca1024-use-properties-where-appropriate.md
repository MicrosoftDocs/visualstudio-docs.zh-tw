---
title: CA1024 建議：適當時使用屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a240a6eea86075bbf7f721f8620b6d135d594c20
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546662"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024:建議在適當時使用屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|類別|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的方法具有以開頭的名稱 `Get` 、不接受任何參數，而且會傳回不是陣列的值。

## <a name="rule-description"></a>規則描述
 在大部分情況下，屬性代表資料和方法會執行動作。 屬性的存取方式就像欄位一樣，讓使用者更容易使用。 如果其中一項條件存在，方法就很適合成為屬性：

- 不接受任何引數，並傳回物件的狀態資訊。

- 接受單一引數，以設定物件狀態的某些部分。

  屬性的行為應該如同欄位一樣。如果方法不能，則不應該將它變更為屬性。 在下列情況下，方法會優於屬性：

- 方法會執行耗時的作業。 方法的 perceivably 速度比設定或取得欄位值所需的時間慢。

- 方法會執行轉換。 存取欄位並不會傳回其所儲存之資料的轉換版本。

- Get 方法具有可觀察的副作用。 抓取欄位的值不會產生任何副作用。

- 執行的順序很重要。 設定欄位的值不會依賴其他作業的出現次數。

- 連續呼叫方法兩次，會產生不同的結果。

- 方法是靜態的，但會傳回可由呼叫端變更的物件。 抓取欄位的值不允許呼叫者變更欄位所儲存的資料。

- 方法會傳回陣列。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將方法變更為屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果方法至少符合先前列出的其中一個準則，請隱藏此規則的警告。

## <a name="controlling-property-expansion-in-the-debugger"></a>控制偵錯工具中的屬性擴充
 程式設計人員避免使用屬性的原因之一，是因為它們不想讓偵錯工具自動將它展開。 例如，屬性可能牽涉到配置大型物件或呼叫 P/Invoke，但實際上可能不會有任何可觀察的副作用。

 您可以藉由套用，讓偵錯工具無法自動擴充屬性 <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName> 。 下列範例顯示此屬性會套用至實例屬性。

```vb
Imports System
Imports System.Diagnostics

Namespace Microsoft.Samples

    Public Class TestClass

        ' [...]

        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _
        Public ReadOnly Property LargeObject() As LargeObject
            Get
                ' Allocate large object
                ' [...]
            End Get
        End Property

    End Class

End Namespace
```

```csharp

      using System;
using System.Diagnostics;

namespace Microsoft.Samples
{
    publicclass TestClass
    {
        // [...]

        [DebuggerBrowsable(DebuggerBrowsableState.Never)]
        public LargeObject LargeObject
        {
            get
            {
                // Allocate large object
                // [...]

        }
    }
}
```

## <a name="example"></a>範例
 下列範例包含數個應該轉換成屬性的方法，而幾個則不應該，因為它們的行為與欄位不一樣。

 [!code-csharp[FxCop.Design.MethodsProperties#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.MethodsProperties/cs/FxCop.Design.MethodsProperties.cs#1)]
