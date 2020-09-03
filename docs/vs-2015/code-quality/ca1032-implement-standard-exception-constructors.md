---
title: CA1032 必須：實行標準例外狀況的函式 |Microsoft Docs
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
ms.openlocfilehash: 61b0157200ddff4cb8335118b30832a0c8950f65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542281"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032:必須實作標準例外狀況建構函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|類別|Microsoft. 設計|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 類型會延伸 <xref:System.Exception?displayProperty=fullName> ，且不會宣告所有必要的函式。

## <a name="rule-description"></a>規則描述
 例外狀況類型必須執行下列的函式：

- 公用 NewException ( # A1

- 公用 NewException (字串) 

- public NewException (字串，例外狀況) 

- protected 或私用 NewException (SerializationInfo、StreamingCoNtext) 

  無法提供整組的建構函式會導致難以正確地處理例外狀況。 例如，具有簽章的函式 `NewException(string, Exception)` 會用來建立其他例外狀況所造成的例外狀況。 如果沒有這個函式，您就無法建立並擲回自訂例外狀況的實例，其中包含內部 (的嵌套) 例外狀況，這是 managed 程式碼在這種情況下的用途。 前三個例外狀況的函式是依慣例公開的。 第四個函式會在未密封類別中受到保護，並在密封類別中受到私用。 如需詳細資訊，請參閱[CA2229：執行序列化](../code-quality/ca2229-implement-serialization-constructors.md)函式

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將遺漏的函式新增至例外狀況，並確定它們具有正確的存取範圍。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 使用公用函式的不同存取層級時，可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例包含違反此規則的例外狀況類型，以及正確實作為的例外狀況類型。

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionMultipleCtors/cs/FxCop.Design.ExceptionMultipleCtors.cs#1)]
