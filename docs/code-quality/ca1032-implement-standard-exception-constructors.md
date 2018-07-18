---
title: CA1032：必須實作標準例外狀況建構函式
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b6cd6922cae5e2d182a279e2d1637a19f8572468
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
ms.locfileid: "34454748"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032：必須實作標準例外狀況建構函式

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|分類|Microsoft.Design|
|中斷變更|非中斷|

## <a name="cause"></a>原因

型別擴充<xref:System.Exception?displayProperty=fullName>但不會宣告所有必要的建構函式。

## <a name="rule-description"></a>規則描述

例外狀況類型必須實作下列三個建構函式：

- 公用 NewException()

- 公用 NewException(string)

- 公用 NewException （字串、 例外狀況）

此外，如果您執行舊版 FxCop 靜態程式碼分析做為相對於[roslyn FxCop 分析器](../code-quality/roslyn-analyzers-overview.md)，如果沒有第四個建構函式也會產生違規：

- 受保護或私用 NewException （SerializationInfo，StreamingContext）

無法提供整組的建構函式會導致難以正確地處理例外狀況。 例如，建構函式的簽章`NewException(string, Exception)`用來建立其他的例外狀況所造成的例外狀況。 沒有這個建構函式，您無法建立和擲回自訂例外狀況，其中包含內部 （巢狀） 例外狀況，也就是 managed 程式碼應該在這種情況下執行的執行個體。

第三個例外狀況建構函式是公用的慣例。 第四個建構函式是在未密封的類別中，受保護與私用在密封類別。 如需詳細資訊，請參閱[CA2229： 實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，加入遺漏的建構函式的例外狀況，並確定它們有正確的存取範圍。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它可以安全地隱藏此規則的警告，違規因使用不同的存取層級的公用建構函式。 此外，也可以隱藏的警告`NewException(SerializationInfo, StreamingContext)`建構函式，如果您正在建立可攜式類別程式庫 (PCL)。

## <a name="example"></a>範例

下列範例包含違反此規則的例外狀況類型以及已正確地實作的例外狀況類型。

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>另請參閱

[CA2229：必須實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)