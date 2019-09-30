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
ms.openlocfilehash: b52f4412b1b048c41033f74200828f70361c1ea3
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232497"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121:靜態建構函式應該為私用的

|||
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|分類|Microsoft.Security|
|重大變更|中斷|

## <a name="cause"></a>原因

類型具有非私用的靜態函式。

## <a name="rule-description"></a>規則描述

靜態的函式（也稱為類別的函式）是用來初始化型別。 系統會在建立類型的第一個執行個體或參考任何靜態成員之前呼叫靜態建構函式。 使用者無法控制呼叫靜態函式的時間。 如果靜態建構函式不是私用的，則可由系統以外的程式碼呼叫。 視建構函式中執行的作業而定，這會造成非預期的行為。

C#和 Visual Basic 編譯器會強制執行此規則。

## <a name="how-to-fix-violations"></a>如何修正違規

違規通常是由下列其中一個動作所造成：

- 您已為您的類型定義靜態的函式，但未將它設為私用。

- 程式設計語言編譯器已將預設的靜態函式新增至您的類型，但未將它設為私用。

若要修正第一種違規，請將您的靜態函式設為私用。 若要修正第二種類型，請將私用的靜態函式新增至您的類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏這些違規。 如果您的軟體設計需要明確呼叫靜態的函式，則設計可能會包含嚴重的缺陷，而且應該加以檢查。