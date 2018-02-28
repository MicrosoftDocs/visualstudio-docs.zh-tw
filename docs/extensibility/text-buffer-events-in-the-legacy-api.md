---
title: "在舊版 API 中的文字緩衝區事件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7e7847cdca2065cadd6adaf0d4b3e6ea10444725
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="text-buffer-events-in-the-legacy-api"></a>在舊版 API 中的文字緩衝區事件
文字緩衝區物件發出數個不同的事件可讓您回應不同的情況。  
  
 當您使用舊版的 API 時，您應該實作下列介面以接收通知的文字緩衝的變更。 公開介面，以使用您建立文字緩衝區`IConnectionPointContainer`上要接收通知列的文字緩衝介面變更緩衝區中。 如需詳細資訊，請參閱[How to： 文字緩衝區使用註冊事件舊版 API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)。 如果是`IVsTextStreamEvents`或`IVsTextLinesEvents`介面，會傳回的變更可能是一個或 two 維度座標中，分別。  
  
## <a name="text-buffer-interfaces"></a>文字緩衝區介面  
 以下是文字緩衝區物件所實作的介面。  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|讓您建立複合的動作 （也就是動作會分組在單一復原/取消復原單位）。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|可讓文字緩衝區所管理的文件資料的持續性。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|提供基本的服務。許多用戶端使用。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|提供讀取和寫入功能使用二維座標。 繼承自 `IVsTextBuffer`。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|提供快速、 在緩衝區中的文字資料流為導向的循序存取。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|提供讀取和寫入使用一維座標的功能。 繼承自 `IVsTextBuffer`。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|提供存取的屬性泛型集合。 名稱或 moniker 時，緩衝區的最重要的屬性。 您可以儲存在緩衝區中，使用此介面的隨機資料，建立 GUID，並使用它做為索引鍵。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|支援的連接點事件。|  
  
## <a name="text-buffer-event-interfaces"></a>文字緩衝區事件介面  
 以下是文字緩衝區事件通知的介面。  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|新語言服務相關聯的文字緩衝區時，通知用戶端。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|初始化文字緩衝區時，變更文字緩衝區中的資料時，通知用戶端。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|通知用戶端的基礎文字緩衝區一維座標中的變更。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|通知用戶端的基礎文字緩衝區二維座標中的變更。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|通知用戶端的使用者資料的變更。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|通知用戶端的最後一個認可手勢來觸發事件，並提供文字已變更的範圍。 `IVsPreliminaryTextChangeCommitEvents`介面不會引發以回應復原或取消復原命令。 針對已復原管理員的緩衝區只引發事件。 `IVsPreliminaryTextChangeCommitEvents`引發之前其他事件，例如美化，若要確定其他事件認可變更之前不要變更文字。 VSPackage 必須監視 `IVsPreliminaryTextChangeCommitEvents`介面或`IVsFinalTextChangeCommitEvents`介面，但非兩者。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|通知用戶端的最後一個認可手勢來觸發事件，並提供文字已變更的範圍。 `IVsFinalTextChangeCommitEvents`介面不會引發以回應復原或取消復原命令。 針對已復原管理員的緩衝區只引發事件。 `IVsFinalTextChangeCommitEvents`適用於只能由語言服務或其他擁有完整控制權編輯的物件。 VSPackage 必須監視 `IVsPreliminaryTextChangeCommitEvents`介面或`IVsFinalTextChangeCommitEvents`介面，但非兩者。|  
  
## <a name="see-also"></a>請參閱  
 [使用舊版 API 存取文字緩衝區](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [如何： 文字緩衝區使用註冊事件舊版應用程式開發介面](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)