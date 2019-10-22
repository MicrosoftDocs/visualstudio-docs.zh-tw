---
title: CA1806：不要忽略方法結果 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f68ab71d9ce4fab1b0612f15d866c58e302a317e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671499"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806：不要忽略方法的結果
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotIgnoreMethodResults|
|CheckId|CA1806|
|Category|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 此警告有幾個可能的原因：

- 已建立新的物件，但從未使用過。

- 會呼叫建立並傳回新字串的方法，而且永遠不會使用新的字串。

- COM 或 P/Invoke 方法，會傳回從未使用的 HRESULT 或錯誤碼。 規則描述

  不需要建立物件，且未使用物件的相關垃圾收集會降低效能。

  字串是不變的，而 ToUpper 之類的方法會傳回字串的新實例，而不是修改呼叫方法中的字串實例。

  忽略 HRESULT 或錯誤碼可能會導致錯誤狀況或資源不足的狀況發生非預期的行為。

## <a name="how-to-fix-violations"></a>如何修正違規
 如果方法 A 建立從未使用之 B 物件的新實例，請將實例當做引數傳遞至另一個方法，或將實例指派給變數。 如果不需要建立物件，請移除它。-或-

 如果方法 A 會呼叫方法 B，但不會使用方法 B 傳回的新字串實例。 將實例當做引數傳遞至另一個方法，並將實例指派給變數。 或移除不必要的呼叫。

 -或-

 如果方法 A 呼叫方法 B，但未使用方法傳回的 HRESULT 或錯誤碼。 使用條件陳述式中的結果、將結果指派給變數，或將它當做引數傳遞至另一個方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 除非建立物件的動作有某種用途，否則請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示的類別會忽略呼叫字串. Trim 的結果。

<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  -->

## <a name="example"></a>範例
 下列範例會藉由指派字串的結果來修正先前的違規，並將其傳回給呼叫它的變數。

<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  -->

## <a name="example"></a>範例
 下列範例顯示不使用它所建立之物件的方法。

> [!NOTE]
> Visual Basic 中無法重現此違規。

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cpp/FxCop.Usage.DoNotIgnoreMethodResults3.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cs/FxCop.Usage.DoNotIgnoreMethodResults3.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/vb/FxCop.Usage.DoNotIgnoreMethodResults3.vb#1)]

## <a name="example"></a>範例
 下列範例會藉由移除不必要的物件建立來修正先前的違規。

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cpp/FxCop.Usage.DoNotIgnoreMethodResults4.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cs/FxCop.Usage.DoNotIgnoreMethodResults4.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/vb/FxCop.Usage.DoNotIgnoreMethodResults4.vb#1)]

## <a name="example"></a>範例
 下列範例顯示的方法會忽略 native 方法 GetShortPathName 所傳回的錯誤碼。

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cpp/FxCop.Usage.DoNotIgnoreMethodResults5.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cs/FxCop.Usage.DoNotIgnoreMethodResults5.cs#1)]

## <a name="example"></a>範例
 下列範例會檢查錯誤碼，並在呼叫失敗時擲回例外狀況，藉以修正先前的違規。

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cpp/FxCop.Usage.DoNotIgnoreMethodResults6.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cs/FxCop.Usage.DoNotIgnoreMethodResults6.cs#1)]