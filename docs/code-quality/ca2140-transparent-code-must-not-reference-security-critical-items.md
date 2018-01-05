---
title: "CA2140： 透明程式碼不可以參考安全性關鍵項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2129
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2140
helpviewer_keywords:
- CA2140
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2129
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0970bd3a05975707cbbac3f79dbece234adb16ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140：透明程式碼不可以參考安全性關鍵項目
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|  
|CheckId|CA2140|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 透明方法：  
  
-   處理安全性關鍵的安全性例外狀況類型  
  
-   已標示為安全性關鍵類型的參數  
  
-   具有安全性關鍵條件約束的泛型參數  
  
-   具有安全性關鍵類型的本機變數  
  
-   參考標示為安全性關鍵的類型  
  
-   呼叫會標示為安全性關鍵的方法  
  
-   參考標示為安全性關鍵的欄位  
  
-   傳回已標示為安全性關鍵的類型  
  
## <a name="rule-description"></a>規則描述  
 標示與程式碼項目<xref:System.Security.SecurityCriticalAttribute>屬性是安全性關鍵。 透明方法不能使用安全性關鍵項目。 如果透明類型嘗試使用安全性關鍵類型<xref:System.TypeAccessException>， <xref:System.MethodAccessException> ，或<xref:System.FieldAccessException>，就會引發。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，執行下列其中一項：  
  
-   將會使用安全性關鍵程式碼與程式碼項目標記<xref:System.Security.SecurityCriticalAttribute>屬性  
  
     \-或-  
  
-   移除<xref:System.Security.SecurityCriticalAttribute>屬性從程式碼項目會標示為安全性關鍵，而是將它們與標記<xref:System.Security.SecuritySafeCriticalAttribute>或<xref:System.Security.SecurityTransparentAttribute>屬性。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 在下列範例中，透明方法會嘗試參考安全性關鍵泛型集合、 安全性關鍵欄位，與安全性關鍵方法。  
  
 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityCriticalAttribute>   
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityTreatAsSafeAttribute>   
 <xref:System.Security?displayProperty=fullName>