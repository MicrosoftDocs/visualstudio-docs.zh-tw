---
title: CA1040:避免使用空的介面
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 726953de0a92c0237ecaf7b724d9586a5d0f4c16
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57868726"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040:避免使用空的介面

|||
|-|-|
|TypeName|AvoidEmptyInterfaces|
|CheckId|CA1040|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因

介面不會宣告任何成員或實作兩個或多個其他介面。

根據預設，此規則只會查看外部可見的介面，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

介面是用來定義一組可提供行為或程式使用合約的成員。 不論類型出現在繼承階層架構 (Inheritance Hierarchy) 中的何處，任何類型都可以採用介面所描述的功能。 類型會實作介面，方法是提供介面成員的實作。 空的介面並未定義任何成員。 因此，它不會定義可以實作的合約。

如果您的設計包含空白預期類型的介面實作，您可能使用介面作為標記或用來識別類型的群組。 如果這個識別會在執行階段，若要完成這項作業的正確方式是使用自訂屬性。 使用存在該屬性中，不存在或屬性的屬性，來識別目標類型。 如果識別必須發生在編譯時期，它可接受使用空的介面。

## <a name="how-to-fix-violations"></a>如何修正違規

移除介面，或將成員加入至它。 如果空的介面來標示一組型別，取代介面的自訂屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它可安全地隱藏此規則的警告，介面用來識別在編譯時期的一組型別時。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```
dotnet_code_quality.ca1040.api_surface = private, internal
```

此類別 （設計） 中，您可以設定此選項，只是這項規則，所有規則，或所有的規則。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>範例

下列範例會顯示空的介面。

[!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
[!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
[!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]