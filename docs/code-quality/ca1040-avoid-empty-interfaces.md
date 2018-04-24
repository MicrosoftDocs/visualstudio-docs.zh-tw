---
title: CA1040：避免空的介面
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 247344cac2f2f36d1db28d1fe217cbfa5d9b6234
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040：避免空的介面
|||
|-|-|
|TypeName|AvoidEmptyInterfaces|
|CheckId|CA1040|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 介面不宣告任何成員，或必須實作兩個或多個其他介面。

## <a name="rule-description"></a>規則描述
 介面是用來定義一組可提供行為或程式使用合約的成員。 不論類型出現在繼承階層架構 (Inheritance Hierarchy) 中的何處，任何類型都可以採用介面所描述的功能。 類型會實作介面，方法是提供介面成員的實作。 空白介面並未定義任何成員。 因此，它並未定義可以實作的合約。

 如果您的設計包含空白應介面的型別實作時，可能使用的介面標記為識別型別群組的方式。 如果這個識別就會發生在執行階段中，完成這項作業的正確方式是使用自訂屬性。 使用存在此屬性，不存在或屬性的屬性，來識別目標類型。 如果識別必須發生在編譯時期，則接受使用空的介面。

## <a name="how-to-fix-violations"></a>如何修正違規
 移除介面，或是將成員加入它。 如果空的介面用來標示一組型別，取代為自訂屬性的介面。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可以安全地介面用來識別在編譯時期的一組型別時隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示空的介面。

 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]