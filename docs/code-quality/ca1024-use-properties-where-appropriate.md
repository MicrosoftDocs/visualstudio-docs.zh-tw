---
title: CA1024:建議在適當時使用屬性
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e4008872a7cb96386ef702d21ba8a18d96037d83
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57869253"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024:建議在適當時使用屬性

|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因

方法具有名稱開頭`Get`、 不採用任何參數和傳回值，這個值不是陣列。

根據預設，此規則只會查看公用和受保護的方法，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

在大部分情況下，屬性代表資料，方法執行動作。 屬性與欄位類似，讓它們可使用的工作變得更容易存取。 方法是成為屬性，若符合下列條件之一，則的良好候選項目：

- 不接受引數，並傳回物件的狀態資訊。

- 接受單一引數來設定物件狀態的某些部分。

屬性應該如同它們是欄位，如果方法無法處理，它應該不會變更的屬性。 方法是優於在下列情況中的屬性：

- 這個方法會執行耗時的作業。 此方法為感覺比所需的設定或取得欄位的值時間。

- 這個方法會執行轉換。 存取欄位不會傳回轉換的版本，它會將儲存的資料。

- Get 方法具有可預見的副作用。 擷取欄位的值不會產生任何副作用。

- 執行的順序很重要。 設定欄位的值不需要其他作業一次。

- 連續兩次呼叫方法時，會建立不同的結果。

- 方法是靜態的但是會傳回呼叫者可以變更的物件。 擷取欄位的值不允許呼叫端將變更儲存欄位的資料。

- 方法會傳回陣列。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請將方法變更為屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果方法會符合至少其中一個先前所列的準則，則隱藏此規則的警告。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```
dotnet_code_quality.ca1024.api_surface = private, internal
```

此類別 （設計） 中，您可以設定此選項，只是這項規則，所有規則，或所有的規則。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="control-property-expansion-in-the-debugger"></a>在 偵錯工具中的控制項屬性擴充

程式設計師可讓您避免使用屬性的其中一個原因是因為不想偵錯工具自動展開它。 例如，配置大型物件或呼叫 P/Invoke，可能會牽涉到的屬性，但它可能實際上沒有任何可預見的副作用。

您可以藉由套用防止偵錯工具從 autoexpanding 屬性<xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>。 下列範例示範套用至執行個體屬性的這個屬性。

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
}
```

## <a name="example"></a>範例

下列範例包含數種方法，應該轉換成屬性，以及數個，應該不是因為它們不與欄位類似的行為。

[!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]