---
title: CA2136：成員不應該具有衝突的透明度注釋 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f2fbb856ff53552ab99dabd4f650e9fd7f62a088
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602974"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136：成員不應該具有衝突的透明度附註
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|Category|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 當類型成員標記的 <xref:System.Security> 安全性屬性的透明度與成員容器的安全性屬性不同時，就會引發此規則。

## <a name="rule-description"></a>規則描述
 透明度屬性會從較大範圍的程式碼項目套用至較小範圍的項目。 範圍較大之程式碼項目的透明度屬性優先於第一個項目中所包含之程式碼項目的透明度屬性。 例如，標記為 <xref:System.Security.SecurityCriticalAttribute> 屬性的類別不能包含標記為 <xref:System.Security.SecuritySafeCriticalAttribute> 屬性的方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此違規，請從範圍較低的程式碼專案中移除安全性屬性，或將其屬性變更為與包含的程式碼專案相同。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 在下列範例中，方法會標記為 <xref:System.Security.SecuritySafeCriticalAttribute> 屬性，而它是標記為 <xref:System.Security.SecurityCriticalAttribute> 屬性之類別的成員。 應該移除安全性安全屬性。

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2136.transparencyannotationsshouldnotconflict/cs/ca2136 - transparencyannotationsshouldnotconflict.cs#1)]
