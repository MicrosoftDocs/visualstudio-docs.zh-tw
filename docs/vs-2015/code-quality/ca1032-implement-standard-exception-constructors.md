---
title: CA1032:實作標準例外狀況建構函式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c59da56304a5d1d8f2cca7eaf886fd5ebc37f8ef
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941038"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032:必須實作標準例外狀況建構函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|分類|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因
 型別擴充<xref:System.Exception?displayProperty=fullName>和未宣告所有必要建構函式。

## <a name="rule-description"></a>規則描述
 例外狀況類型必須實作下列建構函式：

- public NewException()

- public NewException(string)

- public NewException(string, Exception)

- 受保護或私用 NewException （SerializationInfo，StreamingContext）

  無法提供整組的建構函式會導致難以正確地處理例外狀況。 例如，建構函式簽章`NewException(string, Exception)`用來建立其他例外狀況所造成的例外狀況。 沒有這個建構函式無法建立及擲回自訂例外狀況，其中包含內部 （巢狀的） 例外狀況的執行個體，這是哪些受管理的程式碼應該在這種情況下。 第三個例外狀況建構函式是公用的慣例。 第四個建構函式是在未密封的類別中，受保護和密封類別中私用。 如需詳細資訊，請參閱[CA2229:必須實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，加入遺漏的建構函式例外狀況，並確定它們有正確的存取範圍。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它是安全違規因使用不同的存取層級的公用建構函式時隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例包含違反此規則的例外狀況類型以及已正確地實作的例外狀況類型。

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionMultipleCtors/cs/FxCop.Design.ExceptionMultipleCtors.cs#1)]
