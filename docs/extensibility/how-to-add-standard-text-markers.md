---
title: "如何： 加入標準文字標記 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1fb92185dd2efee7f42ce1ba4d97435e0b2e8a68
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-standard-text-markers"></a>如何： 加入標準文字標記
使用下列程序建立隨附的預設文字標記類型的其中一個[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器。  
  
### <a name="to-create-a-text-marker"></a>若要建立文字標記  
  
1.  視您使用的一個或兩個-維座標系統，請呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>方法或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>方法來建立新的文字標記。  
  
     在這個方法呼叫中，指定標記類型，以透過，建立標記的文字範圍的和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>介面。 然後這個方法會將指標傳回至新建立的文字標記。 標記類型取自<xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE>列舉型別。 指定<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>介面，如果您想要收到標記事件的通知。  
  
    > [!NOTE]
    >  在主要 UI 執行緒上只能建立文字標記。 核心編輯器是要建立文字標記的文字緩衝的內容，而文字緩衝區不是安全執行緒。  
  
## <a name="adding-a-custom-command"></a>加入自訂命令  
 實作`IVsTextMarkerClient`介面，並提供給它的指標，從標記增強了數種方式的標記行為。 首先，這可讓您為您的標記提供提示，並執行命令。 這也可讓您接收事件通知，針對個別的標記，並透過標記建立自訂的內容功能表。 若要將自訂命令加入至標記內容功能表使用下列程序。  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>若要將自訂命令加入至內容功能表  
  
1.  內容功能表會出現之前，環境會呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A>方法和傳遞您的指標，text 標記會受到影響的內容功能表中的命令項目數目。  
  
     例如，內容功能表上的特定中斷點的命令包含**移除中斷點**透過**新增中斷點**，如下列螢幕擷取畫面中顯示。  
  
     ![標記操作功能表](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2.  傳回識別自訂命令的名稱部分文字。 例如，**移除中斷點**如果環境未已經提供它可能是自訂的命令。 您也將傳遞回命令是否支援、 可用和已啟用，及/或-關閉切換。 環境會使用這項資訊以顯示內容功能表中的自訂命令的正確方式。  
  
3.  若要執行命令時，環境呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A>方法，您將指標傳遞至文字標記，而從內容功能表中所指定的命令數目。  
  
     執行任何動作的文字標記您的自訂命令規定使用這個呼叫的這項資訊。  
  
## <a name="see-also"></a>另請參閱  
 [使用文字標記與舊版應用程式開發介面](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [如何： 實作錯誤標記](../extensibility/how-to-implement-error-markers.md)   
 [如何： 建立自訂文字標記](../extensibility/how-to-create-custom-text-markers.md)   
 [如何： 使用文字標記](../extensibility/how-to-use-text-markers.md)