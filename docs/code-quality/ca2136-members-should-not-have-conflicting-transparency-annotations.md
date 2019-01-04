---
title: CA2136:成員不應該具有衝突的透明度註釋
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3186baa671aba3830d864434a519c6eb820d5204
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53899846"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136:成員不應該具有衝突的透明度註釋

|||
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 與標記類型成員時，就會引發此規則<xref:System.Security>具有成員的容器安全性屬性不同透明度的安全性屬性。

## <a name="rule-description"></a>規則描述
 透明度屬性會從較大範圍的程式碼項目套用至較小範圍的項目。 範圍較大之程式碼項目的透明度屬性優先於第一個項目中所包含之程式碼項目的透明度屬性。 例如，類別標記為<xref:System.Security.SecurityCriticalAttribute>屬性不能包含標示的方法<xref:System.Security.SecuritySafeCriticalAttribute>屬性。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此違規，從程式碼項目具有較低的範圍中移除安全性屬性，或變更其屬性，以包含程式碼項目相同。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏這項規則的警告。

## <a name="example"></a>範例
 在下列範例中，方法會標示<xref:System.Security.SecuritySafeCriticalAttribute>屬性並已標示為類別的成員<xref:System.Security.SecurityCriticalAttribute>屬性。 應移除的安全性的安全屬性。

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]