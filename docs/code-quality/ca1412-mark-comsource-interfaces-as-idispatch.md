---
title: "CA1412： 將 ComSource 介面標記為 IDispatch |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b8a53053588670fef616f4df7633b3a25fb45712
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412：將 ComSource 介面標記為 IDispatch
|||  
|-|-|  
|TypeName|MarkComSourceInterfacesAsIDispatch|  
|CheckId|CA1412|  
|分類|Microsoft.Interoperability|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 類型會標示<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>屬性和至少一個指定的介面未標示為<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>屬性設為`InterfaceIsDispatch`值。  
  
## <a name="rule-description"></a>規則描述  
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>用來識別的事件介面的類別會公開元件物件模型 (COM) 用戶端。 這些介面必須公開為`InterfaceIsIDispatch`讓 Visual Basic 6 COM 用戶端可以接收事件通知。 根據預設，如果介面不標記為<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>屬性，它會公開為雙重介面。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，加入或修改<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>屬性，讓其值設定所指定的所有介面 InterfaceIsIDispatch<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>屬性。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 下列範例會顯示其中一個介面違反了 「 規則類別。  
  
 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA1408：不要使用 AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## <a name="see-also"></a>另請參閱  
 [如何：引發由 COM 接收所處理的事件](http://msdn.microsoft.com/en-us/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd)   
 [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)