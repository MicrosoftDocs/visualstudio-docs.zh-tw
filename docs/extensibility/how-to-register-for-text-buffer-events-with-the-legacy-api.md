---
title: HOW TO：註冊使用舊版 API 的文字緩衝區事件 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e514bdb50343af549e37a068eb138a3d30fd170
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54980007"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>HOW TO：註冊使用舊版 API 的文字緩衝區事件
如果您使用舊版 API 存取的文字緩衝區，您應該註冊文字緩衝區事件，如下列程序中所示。  
  
## <a name="to-advise-text-buffer-events"></a>建議的文字緩衝區事件  
  
1.  其中一個上介面的指標<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>，呼叫`QueryInterface`指標<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>。  
  
2.  呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A>方法，然後在您要註冊的事件的介面 ID 的傳遞。  
  
     例如，如果您想要報名<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>，然後傳入介面 ID 的 IID_IVsTextLinesEvents。  
  
     文字緩衝區將指標傳回至<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>適當連接點物件的介面。  
  
3.  使用這個指標，呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>方法，將指標傳遞給您，您想要註冊，比方說，在事件介面的實作`IVsTextLinesEvents`介面。  
  
     環境傳回 cookie，您可以使用它表示停止接聽事件，藉由呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A>方法。  
  
## <a name="see-also"></a>另請參閱  
 [在舊版的 API 中的文字緩衝區事件](../extensibility/text-buffer-events-in-the-legacy-api.md)