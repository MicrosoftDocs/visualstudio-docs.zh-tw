---
title: CA2121:靜態建構函式應該為私用的
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9aecfe8e0be0f5d32df41b7eb164423fd4d405db
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55939732"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121:靜態建構函式應該為私用的

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

此規則會強制執行 C# 和 Visual Basic 編譯器。

## <a name="how-to-fix-violations"></a>如何修正違規

違規通常是由下列動作之一造成：

- 您為您的型別定義靜態建構函式，並未將它設為私用。

- 程式設計的語言編譯器預設靜態建構函式加入您的型別，以及未將它設為私用。

若要修正第一種違規的情況，請您靜態建構函式私用。 若要修正第二種類型，加入您的型別中的私用靜態建構函式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏這些違規。 如果您的軟體設計需要明確呼叫靜態建構函式，很可能設計包含重大的缺陷，因此應檢閱。