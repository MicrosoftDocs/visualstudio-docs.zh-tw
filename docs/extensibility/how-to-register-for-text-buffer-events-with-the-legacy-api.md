---
title: "如何： 註冊使用舊版 API 的文字緩衝區事件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fabdf30480666ee3bc24bf3d68af4cc0dcc1ccb6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>如何： 文字緩衝區使用註冊事件舊版應用程式開發介面
如果您要使用舊版 API 存取文字緩衝區，您應該註冊的文字緩衝區事件，如下列程序中所示。  
  
### <a name="to-advise-text-buffer-events"></a>通知文字緩衝區事件  
  
1.  其中一個上介面的指標從<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>，呼叫`QueryInterface`指標<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>。  
  
2.  呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A>方法，並傳入您要註冊的事件的介面 ID。  
  
     例如，如果您想要註冊<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>，則在介面 ID 的 IID_IVsTextLinesEvents 中傳遞。  
  
     文字緩衝區將指標傳回至<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>適當的連接點物件的介面。  
  
3.  使用這個指標，呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>方法，您的實作，您想要註冊，例如，事件介面的指標傳遞`IVsTextLinesEvents`介面。  
  
     環境傳回的 cookie，您可以在停止聽候事件藉由呼叫使用<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A>方法。  
  
## <a name="see-also"></a>另請參閱  
 [在舊版 API 中的文字緩衝區事件](../extensibility/text-buffer-events-in-the-legacy-api.md)