---
title: "CA1406： 避免對 Visual Basic 6 用戶端的 Int64 引數 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 10b02338b16dc3bd1c67e3ab11cdd02d3d1ef1be
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406：避免對 Visual Basic 6 用戶端使用 Int64 引數
|||  
|-|-|  
|TypeName|AvoidInt64ArgumentsForVB6Clients|  
|CheckId|CA1406|  
|分類|Microsoft.Interoperability|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 特別標示為可見元件物件模型 (COM) 類型宣告的成員，會採用<xref:System.Int64?displayProperty=fullName>引數。  
  
## <a name="rule-description"></a>規則描述  
 Visual Basic 6 COM 用戶端無法存取 64 位元整數。  
  
 根據預設，以下是為 COM 可見： 組件、 公用型別、 公用的型別中的公用執行個體成員和公用實值型別的所有成員。 不過，若要減少誤判，這項規則要求 COM 可見性的明確指示; 類型包含組件必須標記為<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>設`false`和型別都必須標記為<xref:System.Runtime.InteropServices.ComVisibleAttribute>設`true`。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此參數，其值永遠可以表示為 32 位元整數類資料類型的規則的違規情形，將參數類型變更為<xref:System.Int32?displayProperty=fullName>。 如果參數的值大於可能會以 32 位元整數類資料類型時，請將參數類型變更為<xref:System.Decimal?displayProperty=fullName>。 請注意，兩者<xref:System.Single?displayProperty=fullName>和<xref:System.Double?displayProperty=fullName>失去精確度的上限範圍在<xref:System.Int64>資料型別。 如果成員不是用來為 COM 可見，將它與標記<xref:System.Runtime.InteropServices.ComVisibleAttribute>設`false`。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告，如果是某些 Visual Basic 6 COM 用戶端將不會存取類型。  
  
## <a name="example"></a>範例  
 下列範例顯示違反規則的類型。  
  
 [!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA1413：避免在 COM 可見實值型別中使用非公用欄位](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407：避免在 COM 可見類型中使用靜態成員](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017：組件必須標記 ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>另請參閱  
 [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)   
 [Long 資料類型](/dotnet/visual-basic/language-reference/data-types/long-data-type)