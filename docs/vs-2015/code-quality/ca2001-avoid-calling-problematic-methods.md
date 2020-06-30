---
title: CA2001：避免呼叫有問題的方法 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ba64c27cde5f335f32cca362417078a5c9ed13e3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538576"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001:避免呼叫有問題的方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|類別|Microsoft 可靠性|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 成員呼叫了可能有危險或問題的方法。

## <a name="rule-description"></a>規則描述
 避免進行不必要和潛在危險的方法呼叫。

 當成員呼叫下列其中一種方法時，就會發生此規則違規。

|方法|描述|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|呼叫 GC。Collect 可能會大幅影響應用程式效能，而且很少需要。 如需詳細資訊，請參閱 MSDN 上的多資料[Mariani 的效能趣聞](https://docs.microsoft.com/archive/blogs/ricom/when-to-call-gc-collect)blog 專案。|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread. 暫止和執行緒。因為其無法預期的行為，所以已淘汰。  使用命名空間中的其他類別（ <xref:System.Threading> 例如 <xref:System.Threading.Monitor> 、 <xref:System.Threading.Mutex> 和） <xref:System.Threading.Semaphore> 來同步處理執行緒或保護資源。|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|DangerousGetHandle 方法會造成安全性風險，因為它可能會傳回不正確控制碼。 如需 <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> 有關如何安全地使用 DangerousGetHandle 方法的詳細資訊，請參閱和方法。|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|這些方法可以從非預期的位置載入元件。 例如，如需載入元件之方法的相關資訊，請參閱 Suzanne 庫的 .NET CLR 附注 blog 文章[LoadFile 與 LoadFrom](https://docs.microsoft.com/archive/blogs/suzcook/loadfile-vs-loadfrom) ，然後選擇 MSDN 網站上的系結[內容](https://docs.microsoft.com/archive/blogs/suzcook/choosing-a-binding-context)。|
|[CoSetProxyBlanket](https://msdn.microsoft.com/library/ms692692.aspx) （ole32.lib）<br /><br /> [CoInitializeSecurity](https://msdn.microsoft.com/library/ms693736.aspx) （ole32.lib）|在使用者程式碼開始在 managed 進程中執行時，太晚無法可靠地呼叫 CoSetProxyBlanket。 Common language runtime （CLR）會採取可防止使用者 P/Invoke 成功的初始化動作。<br /><br /> 如果您必須呼叫 managed 應用程式的 CoSetProxyBlanket，建議您使用機器碼（c + +）可執行檔來啟動程式，並在機器碼中呼叫 CoSetProxyBlanket，然後啟動程式中的受控碼應用程式。 （請務必指定執行階段版本號碼）。|

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請移除或取代對危險或問題方法的呼叫。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有在沒有有問題的方法可用的替代專案時，您才應該隱藏此規則中的訊息。

## <a name="see-also"></a>另請參閱
 [可靠性警告](../code-quality/reliability-warnings.md)
