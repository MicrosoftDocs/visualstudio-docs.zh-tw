---
title: CA2006:必須使用 SafeHandle 封裝原生資源
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 0e671deab060346bb998932495e5590f19945eaa
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233095"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006:必須使用 SafeHandle 封裝原生資源

|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|分類|Microsoft.Reliability|
|重大變更|不中斷|

## <a name="cause"></a>原因

Managed 程式碼<xref:System.IntPtr>會使用來存取原生資源。

## <a name="rule-description"></a>規則描述

在 managed `IntPtr`程式碼中使用，可能表示有潛在的安全性和可靠性問題。 所有的`IntPtr`使用都必須經過審查<xref:System.Runtime.InteropServices.SafeHandle> ，以判斷其位置是否需要使用或類似的技術。 如果`IntPtr`代表一些原生資源（例如記憶體、檔案控制代碼或通訊端），則會將 managed 程式碼視為擁有，就會發生問題。 如果受控碼擁有資源，它也必須釋放與它相關聯的原生資源，因為如果無法這樣做，可能會導致資源洩漏。

在這種情況下，如果允許`IntPtr`多執行緒存取，也會存在安全性或可靠性問題，而且提供了釋放所表示`IntPtr`之資源的方法。 這些問題牽涉到資源釋放`IntPtr`上的值回收，同時使用資源的同時也是在另一個執行緒上進行。 這可能會造成競爭情況，其中一個執行緒可以讀取或寫入與錯誤資源相關聯的資料。 例如，如果您的型別將 OS 控制碼儲存`IntPtr`為，並允許使用者同時呼叫使用該控制碼的**關閉**和任何其他方法，而不需要進行某種同步處理，則您的程式碼會有控制碼回收的問題。

這種處理回收的問題可能會導致資料損毀，而且經常會造成安全性弱點。 `SafeHandle`及其同輩類別<xref:System.Runtime.InteropServices.CriticalHandle>提供一種機制，可將原生控制碼封裝至資源，以便避免這樣的執行緒問題。 此外，您可以使用`SafeHandle`及其同輩類別`CriticalHandle`來處理其他執行緒問題，例如，透過呼叫原生方法，謹慎控制包含原生控制碼複本的 managed 物件的存留期。 在這種情況下，您通常可以移除`GC.KeepAlive`對的呼叫。 當您使用`SafeHandle`和時，所產生的效能額外負荷較低的`CriticalHandle`程度，通常可以透過仔細的設計來降低。

## <a name="how-to-fix-violations"></a>如何修正違規

`IntPtr` 將`SafeHandle`使用方式轉換為，以安全地管理原生資源的存取權。 如需範例，請參閱參考文章。<xref:System.Runtime.InteropServices.SafeHandle>

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏這個警告。

## <a name="see-also"></a>另請參閱

- <xref:System.IDisposable>