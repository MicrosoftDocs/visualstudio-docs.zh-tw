---
title: "CA1411: COM 註冊方法不應該為可見 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 67a4d4124ac1aae99327fdcd757db546cb50adfe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411：COM 註冊方法不應該為可見的
|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldNotBeVisible|  
|CheckId|CA1411|  
|分類|Microsoft.Interoperability|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 方法會標示<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>或<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>是外部可見的屬性。  
  
## <a name="rule-description"></a>規則描述  
 組件註冊時使用元件物件模型 (COM)，每個組件中的 COM 可見類型的登錄中加入項目。 方法是，標示<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>和<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>屬性即稱為註冊或取消登錄處理期間，分別執行註冊/取消註冊這些類型的特定的使用者程式碼。 此程式碼不應呼叫這些程序之外。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，變更方法的存取範圍`private`或`internal`(`Friend`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 下列範例會顯示違反規則的兩個方法。  
  
 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA1410：應該和 COM 註冊方法對應](../code-quality/ca1410-com-registration-methods-should-be-matched.md)  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [向 COM 註冊組件](/dotnet/framework/interop/registering-assemblies-with-com)   
 [Regasm.exe (組件登錄工具)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)