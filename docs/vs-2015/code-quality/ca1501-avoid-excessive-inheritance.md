---
title: CA1501：避免過度繼承 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: cf797ad67b7df2eb1f3ba1246e965ed6ebbd586d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547858"
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501:避免在物件間過度繼承
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|AvoidExcessiveInheritance|
|CheckId|CA1501|
|類別|Microsoft 的可維護性|
|中斷變更|中斷|

## <a name="cause"></a>原因
 類型在其繼承階層架構 (Inheritance Hierarchy) 中超過四個層級的深度。

## <a name="rule-description"></a>規則描述
 太深的巢狀類型階層架構可能會難以依循、了解和維護。 此規則會限制對相同模組中階層的分析。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請從繼承階層中較深層的基底類型衍生型別，或消除某些中繼基底類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 隱藏此規則的警告是安全的。 不過，程式碼可能更難維護。 請注意，根據基底類型的可見度，解決此規則的違規可能會產生重大變更。 例如，移除公用基底類型是一項重大變更。

## <a name="example"></a>範例
 下列範例顯示違反規則的類型。

 [!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.ExcessiveInheritance/cs/FxCop.Maintainability.ExcessiveInheritance.cs#1)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.ExcessiveInheritance/vb/FxCop.Maintainability.ExcessiveInheritance.vb#1)]
