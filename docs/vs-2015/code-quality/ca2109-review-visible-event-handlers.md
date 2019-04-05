---
title: CA2109:檢閱顯示的事件處理常式 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 45e741882e8da2b5ed419540e40f3be40278d540
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58942643"
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109:必須檢閱可見的事件處理常式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|CheckId|CA2109|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 偵測到公用或保護的事件處理方法。

## <a name="rule-description"></a>規則描述
 外部可見的事件處理方法會顯示需要檢閱的安全性問題。

 除非有絕對的必要性，否則不應該公開事件處理方法。 事件處理常式，會叫用的公開的方法的委派類型，可以加入至任何事件，只要處理常式和事件簽章相符。 事件可能會引發的任何程式碼，並經常會引發以回應使用者動作，例如按一下按鈕的高度信任的系統程式碼。 加入事件處理方法的安全性檢查不會防止程式碼註冊事件處理常式叫用方法。

 要求無法可靠地保護由事件處理常式叫用方法。 安全性要求協助防範不受信任的呼叫端中的程式碼，藉由檢查呼叫堆疊上的呼叫端。 事件處理常式的方法執行時，將事件處理常式加入至事件的程式碼不一定出現在 呼叫堆疊上。 因此，呼叫堆疊可能只有高度信任的呼叫端叫用事件處理常式方法時。 這會導致事件處理常式方法對成功的要求。 此外，叫用方法時，需要的權限就可能會判斷提示。 基於這些理由，風險不修正此規則的違規情形只會評估檢閱事件處理方法之後。 當您檢閱您的程式碼時，請考慮下列問題：

-   您的事件處理常式不會執行任何危險或可利用來攻擊，例如判斷提示權限，或隱藏 unmanaged 程式碼的權限的作業嗎？

-   什麼是與您的程式碼的安全性威脅，因為它可以隨時執行與只有高度信任的呼叫端在堆疊上的嗎？

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請檢閱中的方法，並評估下列：

-   可以您讓事件處理方法非公用？

-   您可以將所有事件處理常式危險功能嗎？

-   如果加諸安全性要求，怎麼做呢以其他方式？

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 隱藏的警告這項規則只有在仔細的安全性檢閱之後若要確定您的程式碼不會造成安全性威脅。

## <a name="example"></a>範例
 下列程式碼會顯示可能會遭惡意程式碼誤用的事件處理方法。

 [!code-csharp[FxCop.Security.EventSecLib#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.EventSecLib/cs/FxCop.Security.EventSecLib.cs#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> <xref:System.EventArgs?displayProperty=fullName>
 [安全性要求](http://msdn.microsoft.com/324c14f8-54ff-494d-9fd1-bfd20962c8ba)
