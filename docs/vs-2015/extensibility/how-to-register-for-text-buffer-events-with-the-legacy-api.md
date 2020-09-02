---
title: 如何：使用舊版 API 註冊文字緩衝區事件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f36e8dd780788d241e3c286b1bbbe581311b143
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204086"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>如何：使用舊版 API 註冊文字緩衝區事件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您使用舊版 API 存取文字緩衝區，則應該註冊文字緩衝區事件，如下列程式所示。  
  
### <a name="to-advise-text-buffer-events"></a>建議文字緩衝區事件  
  
1. 從的其中一個介面指標 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> ，呼叫的 `QueryInterface` 指標 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> 。  
  
2. 呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> 方法，然後傳入您要註冊之事件的介面識別碼。  
  
     例如，如果您想要註冊 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> ，請傳入 IID_IVsTextLinesEvents 的介面識別碼。  
  
     文字緩衝區會將指標傳回給 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 適當的連接點物件的介面。  
  
3. 使用這個指標，呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> 方法，將指標傳入您要註冊之事件介面的執行，例如 `IVsTextLinesEvents` 介面。  
  
     環境會傳回 cookie，讓您可以藉由呼叫方法來停止接聽事件 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> 。  
  
## <a name="see-also"></a>另請參閱  
 [舊版 API 中的文字緩衝區事件](../extensibility/text-buffer-events-in-the-legacy-api.md)
