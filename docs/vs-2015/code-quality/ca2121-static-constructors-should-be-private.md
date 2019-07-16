---
title: CA2121:靜態建構函式應為私用 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d7894b4ec0039b28a579239605c22c2397c300f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154341"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121:靜態建構函式應該為私用的
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 型別具有不是私用靜態建構函式。

## <a name="rule-description"></a>規則描述
 靜態建構函式，也就是類別建構函式，用來初始化型別。 系統會在建立類型的第一個執行個體或參考任何靜態成員之前呼叫靜態建構函式。 使用者已無法控制當呼叫靜態建構函式。 如果靜態建構函式不是私用的，則可由系統以外的程式碼呼叫。 視建構函式中執行的作業而定，這會造成非預期的行為。

 此規則會強制執行 C# 和 Visual Basic.NET 編譯器。

## <a name="how-to-fix-violations"></a>如何修正違規
 違規通常是由下列動作之一造成：

- 您為您的型別定義靜態建構函式，並未將它設為私用。

- 程式設計的語言編譯器預設靜態建構函式加入您的型別，以及未將它設為私用。

  若要修正第一種違規的情況，請您靜態建構函式私用。 若要修正第二種類型，加入您的型別中的私用靜態建構函式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏這些違規。 如果您的軟體設計需要明確呼叫靜態建構函式，很可能設計包含重大的缺陷，因此應檢閱。
