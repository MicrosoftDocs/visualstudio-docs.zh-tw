---
title: CA2214：不要在函式中呼叫可覆寫的方法 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ad467e880b3281a75db2627108af0e0b2f90ea99
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534455"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214:不要呼叫建構函式中的可覆寫方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|類別|Microsoft. 使用量|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 非密封類型的函式會呼叫其類別中定義的虛擬方法。

## <a name="rule-description"></a>規則描述
 呼叫虛擬方法時，在執行時間之前不會選取執行方法的實際型別。 當函式呼叫虛擬方法時，叫用方法之實例的函式可能尚未執行。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請不要從型別的函式內呼叫類型的虛擬方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 您應該重新設計此函式，以消除對虛擬方法的呼叫。

## <a name="example"></a>範例
 下列範例示範違反此規則的效果。 測試應用程式會建立的實例 `DerivedType` ，這會使其基類 () 的函式 `BadlyConstructedType` 執行。 `BadlyConstructedType`的函式不正確地呼叫虛擬方法 `DoSomething` 。 如輸出所示， `DerivedType.DoSomething()` 會執行，並在執行此函式之前執行 `DerivedType` 。

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 此範例會產生下列輸出。

 **呼叫基底 ctor。** 
**衍生的 >dosomething 稱為-已初始化？沒有** 
 **呼叫衍生的 ctor。**
