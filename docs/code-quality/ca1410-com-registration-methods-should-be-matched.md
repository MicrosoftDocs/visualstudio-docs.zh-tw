---
title: "CA1410： 應該符合 COM 註冊方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 660524e4198a06eb6a7e3d627e28acaa721bf8c2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410：應該符合 COM 註冊方法
|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldBeMatched|  
|CheckId|CA1410|  
|分類|Microsoft.Interoperability|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 類型會宣告方法標示為<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>屬性，但不宣告會以標記的方法<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>屬性，反之亦然。  
  
## <a name="rule-description"></a>規則描述  
 若要建立的元件物件模型 (COM) 用戶端[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]型別，必須先註冊型別。 如果有的話，會以標記的方法<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>執行使用者指定的程式碼的註冊程序期間會呼叫屬性。 對應的方法標示為<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>回復註冊方法的作業的取消註冊程序期間會呼叫屬性。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，加入相對應的登錄或取消註冊方法。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 下列範例顯示違反規則的類型。 加上註解的程式碼會顯示發生違規的修正。  
  
 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA1411：COM 註冊方法不應該為可見的](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [向 COM 註冊組件](/dotnet/framework/interop/registering-assemblies-with-com)   
 [Regasm.exe (組件登錄工具)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)