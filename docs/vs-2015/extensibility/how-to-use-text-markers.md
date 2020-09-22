---
title: 如何：使用文字標記 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25c3c4f3a3d9a253b9ec671892d0d44ccf9ca3ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838937"
---
# <a name="how-to-use-text-markers"></a>如何：使用文字標記
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

可以套用文字標記以編輯 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 物件。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-apply-text-markers"></a>若要套用文字標記  
  
1. 取得類別的實例 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> 。  
  
    > [!NOTE]
    > 核心編輯器會自動將標準文字標記套用至任何正在編輯的檔，而且不需要明確地套用標準文字標記。  
  
2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A>使用 `GUID` 您想要使用之文字標記的來呼叫方法，以取得您感興趣之標記的標記類型識別碼。  
  
    > [!NOTE]
    > 請勿使用 `GUID` 提供文字標記的 VSPackage 或服務。  
  
3. 使用透過呼叫方法所取得的標記類型識別碼 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> 作為參數來呼叫方法， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> 或使用方法將 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> 文字標記套用至指定的文字區域。  
  
#### <a name="to-add-features-to-text-markers"></a>將功能加入至文字標記  
  
1. 您可能會想要將其他功能新增至文字標記，例如工具提示、特殊內容功能表或特殊情況的處理常式。 操作方法：  
  
2. 建立執行介面的物件 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 。  
  
3. 如果需要額外的功能，請 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx> 在執行介面的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> 相同物件上，執行和介面 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 。  
  
4. 將 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 您建立的介面傳遞給方法的呼叫， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> 或 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> 用來將文字標記套用至指定之文字區域的方法。  
  
5. 將內容功能表支援加入至文字標記區域時，必須建立功能表。  
  
     如需如何建立快顯功能表的詳細資訊，請參閱[操作功能表。](../extensibility/context-menus.md)  
  
6. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]環境會呼叫所提供介面的方法（例如 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> 方法），或 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> 視需要呼叫方法。  
  
## <a name="see-also"></a>另請參閱  
 [搭配舊版 API 使用文字標記](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [如何：新增標準文字標記](../extensibility/how-to-add-standard-text-markers.md)   
 [如何：建立自訂文字標記](../extensibility/how-to-create-custom-text-markers.md)   
 [如何：實作錯誤標記](../extensibility/how-to-implement-error-markers.md)
