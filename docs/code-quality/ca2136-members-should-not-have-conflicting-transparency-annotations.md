---
title: CA2136： 成員不應該具有衝突的透明度註釋 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.openlocfilehash: e6b77dfdbb97d54e5ad1ac31d3f5e29a03cd9b54
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136：成員不應該具有衝突的透明度附註
|||  
|-|-|  
|TypeName|TransparencyAnnotationsShouldNotConflict|  
|CheckId|CA2136|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 類型成員已標記時引發此規則<xref:System.Security>具有不同的透明度，成員的容器的安全性屬性的安全性屬性。  
  
## <a name="rule-description"></a>規則描述  
 透明度屬性會從較大範圍的程式碼項目套用至較小範圍的項目。 範圍較大之程式碼項目的透明度屬性優先於第一個項目中所包含之程式碼項目的透明度屬性。 例如，類別標記為<xref:System.Security.SecurityCriticalAttribute>屬性不能包含方法標示為<xref:System.Security.SecuritySafeCriticalAttribute>屬性。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正這種違規，從程式碼項目具有較低的範圍中移除安全性屬性，或變更其屬性，會包含程式碼項目相同。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 在下列範例中，以標記方法<xref:System.Security.SecuritySafeCriticalAttribute>屬性並已標示為類別的成員<xref:System.Security.SecurityCriticalAttribute>屬性。 應移除安全性的安全屬性。  
  
 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]