---
title: CA1806:不要忽略方法的結果
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
author: gewarren
ms.author: gewarren
dev_langs:
- CPP
- CSharp
- VB
manager: jillfra
ms.openlocfilehash: 4ac122534a42cb78b80d1a12004a8db3d1b5b203
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2019
ms.locfileid: "55043631"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806:不要忽略方法的結果

|||
|-|-|
|TypeName|DoNotIgnoreMethodResults|
|CheckId|CA1806|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因

有數個可能的原因，這個警告：

- 已建立新的物件，但從未使用過。

- 呼叫的方法，建立並傳回新字串，以及新字串從未使用過。

- COM 或 P/Invoke 方法會傳回 HRESULT 或錯誤碼的程式碼，不會用到。 規則描述

建立不必要的物件和未使用的物件相關聯的記憶體回收集合會降低效能。

字串是不變，例如 String.ToUpper 方法會傳回字串而非修改字串呼叫方法中的執行個體的新執行個體。

忽略 HRESULT 或錯誤碼可能會導致非預期的行為，在錯誤條件或資源不足狀況。

## <a name="how-to-fix-violations"></a>如何修正違規
 如果方法的建立從未使用過的 B 物件的新執行個體，將執行個體做為引數傳遞給另一個方法，或指派給變數的執行個體。 如果不需要建立的物件，將它移除。-或-

 如果方法 A 呼叫 B，; 方法，但未使用 B 則方法會傳回新字串執行個體。 將執行個體做為引數傳遞給另一個方法，將執行個體指派給變數。 或如果不需要移除的呼叫。

 -或-

 如果方法的呼叫方法，B，但不會使用 HRESULT 或錯誤碼，這個方法傳回。 使用中的條件陳述式的結果、 將結果指派給變數，或將它做為引數傳遞給另一個方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告，除非建立物件的動作有一些用途。

## <a name="example"></a>範例
 下列範例顯示的類別，會忽略呼叫 String.Trim 的結果。

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]

## <a name="example"></a>範例
 下列範例會將前述的違規修正 String.Trim 的結果指派給所呼叫的變數。

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]

## <a name="example"></a>範例
 下列範例會示範不會使用它所建立物件的方法。

> [!NOTE]
> 無法在 Visual Basic 中重現此違規。

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]

## <a name="example"></a>範例
 下列範例會將先前的違規修正藉由移除不必要建立物件。

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)]

<!-- Examples don't exist for the below... -->
<!--
## Example
 The following example shows a method that ignores the error code that the native method GetShortPathName returns.

## Example
 The following example fixes the previous violation by checking the error code and throwing an exception when the call fails.
-->