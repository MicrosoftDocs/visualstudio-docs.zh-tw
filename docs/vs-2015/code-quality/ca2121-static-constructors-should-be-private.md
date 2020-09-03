---
title: CA2121：靜態的函式應為私用 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7f95b33e1391ca755a6c0df261fa2bd05bd3c7a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544309"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121:靜態建構函式應該為私用的
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 類型具有非私用的靜態函式。

## <a name="rule-description"></a>規則描述
 靜態的函式（也稱為類別的函式）是用來初始化型別。 系統會在建立類型的第一個執行個體或參考任何靜態成員之前呼叫靜態建構函式。 使用者無法控制呼叫靜態函式的時機。 如果靜態建構函式不是私用的，則可由系統以外的程式碼呼叫。 視建構函式中執行的作業而定，這會造成非預期的行為。

 C # 和 Visual Basic .NET 編譯器會強制執行此規則。

## <a name="how-to-fix-violations"></a>如何修正違規
 違規的原因通常是下列其中一個動作：

- 您已為您的型別定義了靜態的函式，但未將它設為私用。

- 程式設計語言編譯器將預設靜態的函式新增至您的型別，並不會將它設為私用。

  若要修正第一種違規情形，請將您的靜態函式設為私用。 若要修正第二種類型，請將私用靜態函式新增至您的型別。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏這些違規。 如果您的軟體設計需要明確呼叫靜態的函式，則可能是因為設計包含嚴重的瑕疵，而且應該經過檢查。
