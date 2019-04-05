---
title: CA1009:必須正確宣告事件處理常式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9f3764e7e7965fb9efe46a8404273de9adde4a34
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943472"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009:事件處理常式必須正確宣告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 委派會處理公用或受保護的事件，並沒有正確的簽章、 傳回型別或參數名稱。

## <a name="rule-description"></a>規則描述
 事件處理常式方法會採用兩個參數。 第一個是型別的<xref:System.Object?displayProperty=fullName>且名為 'sender'。 這是引發事件的物件。 第二個參數的類型是<xref:System.EventArgs?displayProperty=fullName>且名為 'e'。 這是與事件相關聯的資料。 例如，如果每當開啟檔案時，會引發事件，事件資料通常會包含檔案的名稱。

 事件處理常式方法不應傳回的值。 這 C# 程式設計語言中，以表示傳回型別`void`。 事件處理常式可以叫用多個物件中的多個方法。 如果傳回值允許方法，每個事件，會發生多個傳回值，並只叫用之最後一個方法的值會是可用。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請更正簽章、 傳回型別或委派的參數名稱。 如需詳細資訊，請參閱下列的範例。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會示範適合用於處理事件的委派。 可以叫用此事件處理常式的方法符合設計指導方針中指定的簽章。 `AlarmEventHandler` 是委派的型別名稱。 `AlarmEventArgs` 從事件資料的基底類別衍生<xref:System.EventArgs>，並保留警示的事件資料。

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cpp/FxCop.Design.EventsTwoParams.cpp#1)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cs/FxCop.Design.EventsTwoParams.cs#1)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/vb/FxCop.Design.EventsTwoParams.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA2109:檢閱顯示的事件處理常式](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>另請參閱
 <xref:System.EventArgs?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>
 [NIB：事件與委派](http://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
