---
title: "CA1413： 避免在 COM 可見實值類型中的非公用欄位 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e8dc7c435d9f853cfb67f7c45f5ec7116ff6fb8e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413：避免在 COM 可見的實值類型中使用非公用欄位
|||  
|-|-|  
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|  
|CheckId|CA1413|  
|分類|Microsoft.Interoperability|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 特別標示為可見元件物件模型 (COM) 實值類型會宣告非公用執行個體欄位。  
  
## <a name="rule-description"></a>規則描述  
 COM 可見實值類型的非公用執行個體欄位對 COM 用戶端而言是可見的。 檢閱資訊，不應該公開，或將會有非預期的設計或安全性影響欄位的內容。  
  
 根據預設，所有公用實值類型會為 COM 可見。 不過，若要減少誤判，這項規則要求 COM 可見性的明確指示的類型。 包含組件必須標記為<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>設`false`和型別都必須標記為<xref:System.Runtime.InteropServices.ComVisibleAttribute>設`true`。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，並保留隱藏的欄位，請將實值類型變更為參考類型或移除<xref:System.Runtime.InteropServices.ComVisibleAttribute>屬性從型別。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告，如果公開欄位可接受的。  
  
## <a name="example"></a>範例  
 下列範例顯示違反規則的類型。  
  
 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA1407：避免在 COM 可見類型中使用靜態成員](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017：組件必須標記 ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>另請參閱  
 [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)   
 [限定互通的 .NET 類型](/dotnet/framework/interop/qualifying-net-types-for-interoperation)