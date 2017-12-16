---
title: "Ca2109： 必須檢閱可見的事件處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6d437aab8e6e6dcdb0500ecfef53c78fab6c1c6b
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2017
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109：必須檢閱可見的事件處理常式
|||  
|-|-|  
|TypeName|ReviewVisibleEventHandlers|  
|CheckId|CA2109|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 偵測到公用或保護的事件處理方法。  
  
## <a name="rule-description"></a>規則描述  
 外部可見的事件處理方法呈現的安全性問題，需要檢閱。  
  
 除非有絕對的必要性，否則不應該公開 (Expose) 事件處理方法。 事件處理常式，公開的方法會叫用的委派類型，可以加入任何事件，只要處理常式和事件簽章相符。 事件可能由任何程式碼所造成，而且經常會引發以回應使用者動作，例如按一下按鈕的高度信任的系統程式碼。 加入事件處理方法的安全性檢查不會阻止程式碼註冊事件處理常式叫用方法。  
  
 要求無法可靠地保護的事件處理常式叫用的方法。 安全性要求協助防止不受信任的呼叫者藉由檢查呼叫堆疊上的呼叫端的程式碼。 事件處理常式的方法執行時，事件加入事件處理常式的程式碼不需要出現呼叫堆疊上。 因此，呼叫堆疊可能只有高度信任的呼叫端叫用事件處理常式方法時。 這會使要求的事件處理常式方法才會成功。 此外，叫用方法時，需要的權限就可能會判斷提示。 基於這些理由，未修正此規則的違規情形的風險只受到檢閱的事件處理方法之後評估。 當您檢閱您的程式碼時，請考慮下列問題：  
  
-   事件處理常式是否執行任何作業都有危險或利用來攻擊，例如判斷提示權限，或隱藏 unmanaged 程式碼權限？  
  
-   什麼是與您的程式碼的安全性威脅，因為它可以在任何時間執行的只有高度信任的呼叫端在堆疊上？  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請檢閱的方法，並評估下列：  
  
-   可以您讓事件處理方法非公用嗎？  
  
-   您可以將所有事件處理常式超出危險的功能嗎？  
  
-   如果會加諸安全性要求，可以達成這點以其他方式？  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 隱藏的警告這項規則只有在仔細的安全性檢閱之後先確定您的程式碼不會造成安全性威脅。  
  
## <a name="example"></a>範例  
 下列程式碼會顯示可能由惡意程式碼誤用的事件處理方法。  
  
 [!code-csharp[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>   
 <xref:System.EventArgs?displayProperty=fullName>   
 