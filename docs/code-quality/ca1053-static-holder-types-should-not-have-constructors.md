---
title: CA1053:靜態預留位置類型不應該包含建構函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 52f04355a266f87a039b8197675c2f5377b840ee
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63388320"
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053:靜態預留位置類型不應該包含建構函式

|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或巢狀公用類型只宣告靜態成員，而且具有公用或保護的預設建構函式。

## <a name="rule-description"></a>規則描述
 建構函式不是必要的，因為呼叫靜態成員不需類型的執行個體。 此外，因為型別並沒有非靜態成員，建立執行個體不提供存取任何類型的成員。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除預設建構函式，或設為私用。

> [!NOTE]
> 某些編譯器會自動建立的公用預設建構函式，如果類型沒有定義任何建構函式。 如果這是您的型別，則新增私用的預設建構函式，來排除此違規情形。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 建構函式的存在會建議類型不是靜態型別。

## <a name="example"></a>範例
 下列範例顯示違反此規則的型別。 請注意，沒有預設建構函式的原始程式碼中。 當此程式碼編譯成組件時，C# 編譯器會插入預設建構函式，將會違反此規則。 若要修正此問題，宣告私用建構函式。

 [!code-csharp[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]