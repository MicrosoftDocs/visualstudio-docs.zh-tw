---
title: "CA2143： 透明方法不可以使用安全性要求 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 22adac09d7890f9d15e0bf50f46235f4b48d73dd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143：透明方法不可以使用安全性要求
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotDemand|  
|CheckId|CA2143|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 以宣告方式標記 tranparent 類型或方法<xref:System.Security.Permissions.SecurityAction?displayProperty=fullName>`.Demand`要求或方法呼叫<xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>方法。  
  
## <a name="rule-description"></a>規則描述  
 安全性透明程式碼不應負責驗證作業的安全性，因此不應要求權限。 安全性透明程式碼應使用完整的要求做出安全性決策，而且安全關鍵程式碼不應依賴透明程式碼提出完全要求。 執行安全性檢查，例如安全性要求，任何程式碼應改為安全關鍵。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 一般情況下，若要修正此規則的違規情形，將方法標示與<xref:System.Security.SecuritySafeCriticalAttribute>屬性。 您也可以移除要求。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 因為是透明方法會讓宣告式安全性要求，在下列程式碼檔案的規則。  
  
 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [CA2142：透明程式碼不可以使用 LinkDemand 加以保護](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)