---
title: 在舊版 API 中的文字緩衝區事件 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c3db7d7a4b2c52e4b831078f789dea75c73b337
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218721"
---
# <a name="text-buffer-events-in-the-legacy-api"></a>在舊版 API 中的文字緩衝區事件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

文字緩衝區物件會發出數個不同的事件，讓您能夠回應不同的情況。  
  
 當您使用舊版 API 時，您應該實作下列介面以接收通知的文字緩衝區變更。 公開介面，以文字緩衝區使用`IConnectionPointContainer`文字緩衝區，以接收通知列上的介面變更緩衝區。 如需詳細資訊，請參閱 <<c0> [ 如何： 註冊使用舊版 API 的文字緩衝區事件](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)。 若是`IVsTextStreamEvents`或`IVsTextLinesEvents`介面，會傳回的變更可能是一個或 two 維度座標中，分別。  
  
## <a name="text-buffer-interfaces"></a>文字緩衝區介面  
 以下是文字緩衝區物件所實作的介面。  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|讓您建立複合的動作 （也就是動作會分組放入單一復原/取消復原單位）。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|可讓受管理的文字緩衝的文件資料的持續性。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|提供基本的服務;許多用戶端使用。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|提供讀取和寫入功能使用二維座標。 繼承自 `IVsTextBuffer`。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|提供快速、 在緩衝區中的文字資料流為導向的循序存取。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|提供讀取和寫入使用一維座標的功能。 繼承自 `IVsTextBuffer`。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|提供存取權之屬性的泛型集合。 名稱或 moniker，緩衝區的最重要的屬性。 您可以儲存在緩衝區中，使用此介面的隨機資料，建立 GUID，並使用它做為索引鍵。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|支援的連接點事件。|  
  
## <a name="text-buffer-event-interfaces"></a>文字緩衝區事件介面  
 以下是文字緩衝區事件通知的介面。  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|新的語言服務與文字緩衝區相關聯時，通知用戶端。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|初始化文字緩衝區時，並對文字緩衝區中的資料變更時，通知用戶端。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|通知用戶端的基礎文字緩衝區一維座標中的變更。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|通知用戶端的基礎文字緩衝區二維座標中的變更。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|通知用戶端的使用者資料的變更。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|通知用戶端的最後一個認可手勢來觸發事件，並提供變更的文字範圍。 `IVsPreliminaryTextChangeCommitEvents`介面並不會引發以復原或重做命令的回應。 事件才會觸發已復原管理員的緩衝區。 `IVsPreliminaryTextChangeCommitEvents` 會引發其他事件，例如美化排列之前, 若要確定其他事件不會改變文字認可變更之前。 VSPackage 必須監視其中一個`IVsPreliminaryTextChangeCommitEvents`介面或`IVsFinalTextChangeCommitEvents`介面，但非兩者。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|通知用戶端的最後一個認可手勢來觸發事件，並提供變更的文字範圍。 `IVsFinalTextChangeCommitEvents`介面並不會引發以復原或重做命令的回應。 事件才會觸發已復原管理員的緩衝區。 `IVsFinalTextChangeCommitEvents` 是用於只能由語言服務或其他擁有完整控制權編輯的物件。 VSPackage 必須監視其中一個`IVsPreliminaryTextChangeCommitEvents`介面或`IVsFinalTextChangeCommitEvents`介面，但非兩者。|  
  
## <a name="see-also"></a>另請參閱  
 [使用舊版 API 存取的文字緩衝區](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [如何：使用舊版 API 註冊文字緩衝區事件](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)

