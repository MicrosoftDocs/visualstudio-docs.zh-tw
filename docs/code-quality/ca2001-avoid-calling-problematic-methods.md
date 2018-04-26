---
title: CA2001：避免呼叫有問題的方法
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc40f51fc0c5c3e2db428252d466760d9f297e23
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001：避免呼叫有問題的方法
|||
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|分類|Microsoft.Reliability|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 成員呼叫了可能有危險或問題的方法。

## <a name="rule-description"></a>規則描述
 避免不必要且有潛在危險的方法呼叫。

 當成員呼叫下列方法之一，就會發生此規則的違規情形。

|方法|描述|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|呼叫 GC。收集會大幅影響應用程式效能，通常不需要。 如需詳細資訊，請參閱[波多黎各 Mariani 效能小知識](http://go.microsoft.com/fwlink/?LinkId=169256)MSDN 上的部落格文章。|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread.Suspend 和 Thread.Resume 已被取代，因為其無法預期的行為。  使用中的其他類別<xref:System.Threading>命名空間，例如<xref:System.Threading.Monitor>， <xref:System.Threading.Mutex>， <xref:System.Threading.Mutex>，和<xref:System.Threading.Semaphore>來同步處理執行緒或保護資源。|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|DangerousGetHandle 方法會有安全性風險，因為它可以傳回不是有效的控制代碼。 請參閱<xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A>和<xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A>如需有關如何安全地使用 DangerousGetHandle 方法的方法。|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|這些方法可以從非預期的位置載入組件。 例如，請參閱 Suzanne Cook.NET CLR 資訊部落格文章[LoadFile vs。LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450)和[選擇繫結的內容](http://go.microsoft.com/fwlink/?LinkId=164451)載入組件的方法的相關資訊的 MSDN 網站上。|
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) (Ole32)<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) (Ole32)|由使用者程式碼開始執行受管理的處理序中時，它是太晚可靠地呼叫 CoSetProxyBlanket。 Common language runtime (CLR) 會初始化動作，可能會導致無法順利執行，使用者 P/Invoke。<br /><br /> 如果您沒有受管理的應用程式呼叫 CoSetProxyBlanket，我們會建議您啟動處理序使用原生程式碼 （c + +） 的可執行檔、 CoSetProxyBlanket 呼叫原生程式碼，並再啟動處理序中的 managed 程式碼應用程式。 （請務必指定執行階段版本號碼）。|

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，移除或取代有危險或問題方法的呼叫。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 僅有問題的方法沒有其他替代可用時，您應該隱藏此規則的訊息。

## <a name="see-also"></a>另請參閱
 [可靠性警告](../code-quality/reliability-warnings.md)