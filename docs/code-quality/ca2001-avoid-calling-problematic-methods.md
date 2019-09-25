---
title: CA2001:避免呼叫有問題的方法
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 95209067f3821b6446b64dc7990e189720d20cea
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233186"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001:避免呼叫有問題的方法

|||
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|分類|Microsoft.Reliability|
|重大變更|不中斷|

## <a name="cause"></a>原因

成員呼叫了可能有危險或問題的方法。

## <a name="rule-description"></a>規則描述

避免進行不必要和潛在危險的方法呼叫。 當成員呼叫下列其中一種方法時，就會發生違反此規則的情況：

|方法|描述|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|呼叫 GC。Collect 可能會大幅影響應用程式效能，而且很少需要。 如需詳細資訊，請參閱 MSDN 上的多資料[Mariani 的效能趣聞](http://go.microsoft.com/fwlink/?LinkId=169256)blog 專案。|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread. 暫止和執行緒。因為其無法預期的行為，所以已淘汰。  使用命名空間中的<xref:System.Threading>其他類別（ <xref:System.Threading.Monitor>例如、 <xref:System.Threading.Mutex>和<xref:System.Threading.Semaphore>）來同步處理執行緒或保護資源。|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|DangerousGetHandle 方法會造成安全性風險，因為它可能會傳回不正確控制碼。 如需有關如何<xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A>安全地使用 DangerousGetHandle 方法的詳細資訊，請參閱和方法。<xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A>|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|這些方法可以從非預期的位置載入元件。 例如，請參閱 Suzanne 庫的 .net CLR 附注 blog 文章[LoadFile 與LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450)和[選擇](http://go.microsoft.com/fwlink/?LinkId=164451)系結內容，以取得載入元件之方法的相關資訊。|
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250)Ole32.lib<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255)Ole32.lib|在使用者程式碼開始在 managed 進程中執行時，太晚無法可靠地呼叫 CoSetProxyBlanket。 Common language runtime （CLR）會採取可防止使用者 P/Invoke 成功的初始化動作。<br /><br /> 如果您必須呼叫 managed 應用程式的 CoSetProxyBlanket，建議您使用機器碼（C++）可執行檔來啟動程式，並在機器碼中呼叫 CoSetProxyBlanket，然後啟動程式中的受控碼應用程式。 （請務必指定執行階段版本號碼）。|

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規，請移除或取代對危險或問題方法的呼叫。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

只有在沒有有問題的方法可用的替代專案時，您才應該隱藏此規則中的訊息。

## <a name="see-also"></a>另請參閱

- [可靠性警告](../code-quality/reliability-warnings.md)