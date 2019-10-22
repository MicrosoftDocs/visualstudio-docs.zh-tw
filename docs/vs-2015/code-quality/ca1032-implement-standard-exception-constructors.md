---
title: CA1032 必須：實標準例外狀況構造函式 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b471387db3ce52944ffad3841dc7e946c4d44873
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661882"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032：必須實作標準例外狀況建構函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Category|Microsoft. Design|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 型別會擴充 <xref:System.Exception?displayProperty=fullName>，而且不會宣告所有必要的函式。

## <a name="rule-description"></a>規則描述
 例外狀況類型必須實作為下列的構造函式：

- 公用 NewException （）

- 公用 NewException （字串）

- 公用 NewException （字串，例外狀況）

- protected 或 private NewException （SerializationInfo，StreamingCoNtext）

  無法提供整組的建構函式會導致難以正確地處理例外狀況。 例如，具有簽章 `NewException(string, Exception)` 的函式會用來建立其他例外狀況所造成的例外狀況。 如果沒有這個函式，您就無法建立和擲回自訂例外狀況的實例，其中包含內部（嵌套）例外狀況，這是 managed 程式碼在這種情況下應該執行的動作。 前三個例外狀況的函式會依照慣例公開。 第四個函式會在未密封的類別中受到保護，並在密封類別中進行私用 如需詳細資訊，請參閱[CA2229：執行序列化](../code-quality/ca2229-implement-serialization-constructors.md)程式

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將遺漏的函式新增至例外狀況，並確定它們具有正確的存取範圍。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當違規是針對公用的函式使用不同的存取層級所造成時，可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例包含違反此規則的例外狀況類型，以及已正確執行的例外狀況類型。

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionMultipleCtors/cs/FxCop.Design.ExceptionMultipleCtors.cs#1)]
