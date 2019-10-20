---
title: CA1009：正確地宣告事件處理常式 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 261013ed844b6c5ba37c544c7745a77378c0c722
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668914"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009：正確宣告事件處理常式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|Category|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 處理公用或受保護事件的委派沒有正確的簽章、傳回型別或參數名稱。

## <a name="rule-description"></a>規則描述
 事件處理常式方法會採用兩個參數。 第一個是類型 <xref:System.Object?displayProperty=fullName>，而且名為「寄件者」。 這是引發事件的物件。 第二個參數的類型為 <xref:System.EventArgs?displayProperty=fullName>，且名稱為 ' e '。 這是與事件相關聯的資料。 例如，如果每次開啟檔案時都會引發事件，則事件資料通常會包含檔案名。

 事件處理常式方法不應該傳回值。 在程式C#設計語言中，這會以傳回類型 `void` 來表示。 事件處理常式可以叫用多個物件中的多個方法。 如果允許方法傳回值，每個事件會發生多個傳回值，而且只會提供所叫用之最後一個方法的值。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請更正委派的簽章、傳回型別或參數名稱。 如需詳細資訊，請參閱下列範例。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示適合處理事件的委派。 這個事件處理常式可以叫用的方法，會符合設計方針中所指定的簽章。 `AlarmEventHandler` 是委派的類型名稱。 `AlarmEventArgs` 衍生自事件資料的基類，<xref:System.EventArgs>，並保存警報事件資料。

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cpp/FxCop.Design.EventsTwoParams.cpp#1)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cs/FxCop.Design.EventsTwoParams.cs#1)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/vb/FxCop.Design.EventsTwoParams.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA2109：必須檢閱可見的事件處理常式](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>請參閱
 <xref:System.EventArgs?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>
 [筆尖：事件和委派](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
