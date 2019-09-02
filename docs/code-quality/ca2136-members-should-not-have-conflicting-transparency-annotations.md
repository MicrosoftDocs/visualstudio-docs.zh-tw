---
title: CA2136:成員不應該具有衝突的透明度註釋
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1dcef8fbfd61b8cd8c946f76d6fcb93dc46f1654
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920636"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136:成員不應該具有衝突的透明度註釋

|||
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
當類型成員標記<xref:System.Security>的安全性屬性具有與成員容器的安全性屬性不同的透明度時, 就會引發此規則。

## <a name="rule-description"></a>規則描述
透明度屬性會從較大範圍的程式碼項目套用至較小範圍的項目。 範圍較大之程式碼項目的透明度屬性優先於第一個項目中所包含之程式碼項目的透明度屬性。 例如, 以<xref:System.Security.SecurityCriticalAttribute>屬性標記的類別不能包含以<xref:System.Security.SecuritySafeCriticalAttribute>屬性標記的方法。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此違規, 請從範圍較低的程式碼專案中移除安全性屬性, 或將其屬性變更為與包含的程式碼專案相同。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
在下列範例中, 方法是以<xref:System.Security.SecuritySafeCriticalAttribute>屬性標記, 而且它是<xref:System.Security.SecurityCriticalAttribute>以屬性標記之類別的成員。 應該移除安全性安全屬性。

[!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]