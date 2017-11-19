---
title: "CA1009： 正確宣告事件處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6191676f94300dfbfafcb8ceb6b0874a8e5b558a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009：正確宣告事件處理常式
|||  
|-|-|  
|TypeName|DeclareEventHandlersCorrectly|  
|CheckId|CA1009|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 處理公用或受保護的事件的委派沒有正確的簽章、 傳回型別或參數名稱。  
  
## <a name="rule-description"></a>規則描述  
 事件處理常式方法會採用兩個參數。 第一個是類型的<xref:System.Object?displayProperty=fullName>且名稱為 'sender'。 這是引發事件的物件。 第二個參數的類型是<xref:System.EventArgs?displayProperty=fullName>且名稱為 'e'。 這是與事件相關聯的資料。 例如，如果每當開啟檔案時，會引發事件，事件資料通常會包含檔案的名稱。  
  
 事件處理常式方法不應該傳回值。 在 C# 程式設計語言，這表示傳回的型別`void`。 事件處理常式可以叫用多個物件中的多個方法。 如果方法允許多個傳回值會針對每個事件，會傳回值，只有最後一個方法被叫用的值就是可用。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請更正簽章、 傳回型別或委派的參數名稱。 如需詳細資訊，請參閱下列範例。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 下列範例示範適用於處理事件的委派。 設計指導方針中指定的簽章符合可以叫用此事件處理常式的方法。 `AlarmEventHandler`是委派的型別名稱。 `AlarmEventArgs`衍生自事件資料的基底類別<xref:System.EventArgs>，並保留警示的事件資料。  
  
 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA2109：必須檢閱可見的事件處理常式](../code-quality/ca2109-review-visible-event-handlers.md)  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.EventArgs?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>   
 [處理和引發事件](/dotnet/standard/events/index)  