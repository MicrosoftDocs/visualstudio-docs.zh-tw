---
title: "使用舊版 API 存取 theText 檢視 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 07ce61a0188802455c4e64b698344c3f275215bd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>使用舊版 API 存取 theText 檢視
文字檢視是儲存在文字緩衝區之文字的呈現。 您可以在下一節中所示，使用舊版 API 存取文字檢視。  
  
## <a name="text-view-object"></a>文字檢視物件  
 每個檢視都與它自己的文字緩衝區，並檢視是在緩衝區中資料的視窗。 下圖顯示的文字檢視物件，因為它由索引鍵的介面<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>。  
  
 ![Visual Studio 文字檢視物件](../extensibility/media/vstextview.gif "vstextview")  
文字檢視物件  
  
 檢視是一種在緩衝區中呈現的文字。 它包含功能，例如自動換行和大綱，以便在檢視中看到的內容不會確切的緩衝區中的文字。  
  
 檢視可讓其他服務或處理程序以攔截連入的命令，並採取行動才能檢視充當他們。 若要這樣做最常見的服務是語言服務。 語言服務可能需要，比方說，攔截 ENTER 鍵，以提供自訂的縮排行為或工具提示的命令。  
  
## <a name="adding-functionality-to-the-text-view"></a>將功能加入至文字檢視  
 您可以自訂文字檢視行為來處理特定的按鍵輸入。 若要攔截按鍵動作，您實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>上您的物件，並提供命令目標 (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) 監視和截距命令。  
  
 文字檢視會針對命令篩選器使用循序的架構。 新的命令篩選器 (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>物件) 的呼叫新增至序列<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>方法。  
  
 [文字] 檢視的事件通知使用來提供`T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents`介面。 實作這個介面上您的用戶端物件來接收通知的文字檢視變更。 使用公開這個介面可文字檢視<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>上文字檢視，以從檢視接收變更通知的介面。  
  
## <a name="see-also"></a>另請參閱  
 [變更檢視設定，以使用舊版 API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [使用文字管理員監控全域設定](../extensibility/using-the-text-manager-to-monitor-global-settings.md)