---
title: CA2121：靜態建構函式應為私用
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4f6eef1097565090fd1b9be572f9a33afed9afed
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121：靜態建構函式應為私用
|||
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 型別具有不是私用靜態建構函式。

## <a name="rule-description"></a>規則描述
 靜態建構函式，也稱為類別建構函式，用來初始化型別。 系統會在建立類型的第一個執行個體或參考任何靜態成員之前呼叫靜態建構函式。 使用者已無法控制當呼叫靜態建構函式。 如果靜態建構函式不是私用的，則可由系統以外的程式碼呼叫。 視建構函式中執行的作業而定，這會造成非預期的行為。

 此規則會強制執行的 C# 和 Visual Basic 編譯器。

## <a name="how-to-fix-violations"></a>如何修正違規
 通常被造成違規的下列動作之一：

-   您為您的型別定義靜態建構函式，並未將它設為私用。

-   程式語言編譯器預設靜態建構函式加入您的類型，未將它設為私用。

 若要修正的第一類的違規情形，讓您靜態建構函式成為 private。 若要修正第二種類型，加入您的型別中的私用靜態建構函式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏這些違規。 如果您的軟體設計需要明確的靜態建構函式呼叫，可能是設計包含嚴重的問題，而且應該檢閱。