---
title: 如何： 使用文字標記 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1f5267295875976ac5370d97f186307637a49b6d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133381"
---
# <a name="how-to-use-text-markers"></a>如何： 使用文字標記
文字標記可以套用至編輯<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>物件。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-apply-text-markers"></a>若要套用標記的文字  
  
1.  取得執行個體<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>類別。  
  
    > [!NOTE]
    >  核心編輯器會自動套用到它正在編輯的任何文件標準文字標記，它應該不需要明確地套用標準文字標記。  
  
2.  取得您感興趣藉由呼叫的標記的標記類型 ID<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A>方法`GUID`文字標記您想要使用。  
  
    > [!NOTE]
    >  請勿使用`GUID`VSPackage 或提供文字標記的服務。  
  
3.  使用標記類型識別碼取得藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A>方法當做參數來呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>方法或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>方法，以套用到指定的文字區域的文字標記。  
  
#### <a name="to-add-features-to-text-markers"></a>若要將功能加入至文字標記  
  
1.  它可能想要將其他功能加入至文字標記，例如工具提示、 特殊的內容功能表上或處理常式的特殊情況。 若要這樣做：  
  
2.  建立實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>介面。  
  
3.  如果想要使用額外的功能，實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>，而<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>介面實作在相同物件上的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>介面。  
  
4.  傳遞<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>建立至呼叫的介面<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>方法或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>用來套用到指定的文字區域的文字標記的方法。  
  
5.  內容功能表支援加入的文字標記區域時就必須建立功能表。  
  
     如需有關如何建立內容功能表，請參閱[操作功能表](../extensibility/context-menus.md)。  
  
6.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境會呼叫的方法提供的介面，例如<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A>方法，或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A>視需要的方法。  
  
## <a name="see-also"></a>另請參閱  
 [使用文字標記與舊版應用程式開發介面](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [如何： 加入標準文字標記](../extensibility/how-to-add-standard-text-markers.md)   
 [如何： 建立自訂文字標記](../extensibility/how-to-create-custom-text-markers.md)   
 [如何： 實作錯誤標記](../extensibility/how-to-implement-error-markers.md)