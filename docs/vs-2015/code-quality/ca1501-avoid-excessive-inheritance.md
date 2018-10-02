---
title: CA1501： 避免過度繼承 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: febffd0b9e2fb0275cab1a8055515c83fade5a12
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588294"
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501：避免過度繼承
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA1501： 避免過度繼承](https://docs.microsoft.com/visualstudio/code-quality/ca1501-avoid-excessive-inheritance)。

|||
|-|-|
|TypeName|AvoidExcessiveInheritance|
|CheckId|CA1501|
|分類|Microsoft.Maintainability|
|中斷變更|中斷|

## <a name="cause"></a>原因
 類型在其繼承階層架構 (Inheritance Hierarchy) 中超過四個層級的深度。

## <a name="rule-description"></a>規則描述
 太深的巢狀類型階層架構可能會難以依循、了解和維護。 此規則會限制分析，以在相同的模組中的階層。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，從較深的階層架構中的基底類型衍生的型別，或排除某些中繼的基底類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏此規則的警告。 不過，程式碼可能會更難維護。 請注意，根據基底類型的可見性，解決違反此規則可能會產生重大變更。 比方說，移除公用基底型別是一項重大變更。

## <a name="example"></a>範例
 下列範例顯示違反規則的型別。

 [!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.ExcessiveInheritance/cs/FxCop.Maintainability.ExcessiveInheritance.cs#1)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.ExcessiveInheritance/vb/FxCop.Maintainability.ExcessiveInheritance.vb#1)]



