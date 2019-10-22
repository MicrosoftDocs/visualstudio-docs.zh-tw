---
title: CA2109 必須：查看可見的事件處理常式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 38a1b7c00c79c7a2e89ef64598b8c409709561ef
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658710"
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109：必須檢視可見的事件處理常式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|CheckId|CA2109|
|Category|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 偵測到公用或保護的事件處理方法。

## <a name="rule-description"></a>規則描述
 外部可見的事件處理方法會顯示需要審查的安全性問題。

 除非有絕對的必要性，否則不應該公開事件處理方法。 只要處理常式和事件簽章相符，就可以將叫用已公開方法的事件處理常式（委派類型）加入至任何事件。 事件可能會由任何程式碼引發，而且通常是由高度信任的系統程式碼引發，以回應使用者動作，例如按一下按鈕。 將安全性檢查新增至事件處理方法，並不會防止程式碼註冊叫用方法的事件處理常式。

 需求無法可靠地保護事件處理常式所叫用的方法。 安全性要求藉由檢查呼叫堆疊上的呼叫端，協助保護來自不受信任呼叫端的程式碼。 當事件處理常式的方法執行時，呼叫堆疊上不一定會有將事件處理常式加入至事件的程式碼。 因此，呼叫堆疊可能只有在叫用事件處理常式方法時，才會有高度信任的呼叫端。 這會導致事件處理常式方法所做的要求成功。 此外，叫用方法時，可能會判斷提示要求的許可權。 基於這些理由，不會修正此規則違規的風險，只能在審查事件處理方法之後進行評估。 當您檢查程式碼時，請考慮下列問題：

- 您的事件處理常式是否會執行任何危險或可利用的作業，例如判斷提示許可權或隱藏非受控碼許可權？

- 您的程式碼有哪些安全性威脅，因為它可以隨時在堆疊上使用高度信任的呼叫端來執行？

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請檢查方法並評估下列各項：

- 您是否可以將事件處理方法設為非公用？

- 您可以從事件處理常式中移動所有危險的功能嗎？

- 如果已強加安全性需求，可以透過其他方式來完成這項作業嗎？

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請只在仔細的安全性審查之後，才隱藏此規則的警告，以確定您的程式碼不會造成安全性威脅。

## <a name="example"></a>範例
 下列程式碼顯示可能被惡意程式碼誤用的事件處理方法。

 [!code-csharp[FxCop.Security.EventSecLib#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.EventSecLib/cs/FxCop.Security.EventSecLib.cs#1)]

## <a name="see-also"></a>請參閱
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> <xref:System.EventArgs?displayProperty=fullName>
 [安全性要求](https://msdn.microsoft.com/324c14f8-54ff-494d-9fd1-bfd20962c8ba)
