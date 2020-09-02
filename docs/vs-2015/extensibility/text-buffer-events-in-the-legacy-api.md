---
title: 舊版 API 中的文字緩衝區事件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e82fa31ca435d0c850a4d9e75e927cff9613b046
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186410"
---
# <a name="text-buffer-events-in-the-legacy-api"></a>舊版 API 中的文字緩衝區事件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

文字緩衝區物件會發出數個不同的事件，讓您能夠回應不同的情況。  
  
 當您使用舊版 API 時，您應該執行下列介面，以便接收文字緩衝區變更的通知。 使用 `IConnectionPointContainer` 文字緩衝區上的介面，從緩衝區接收行變更的通知，以將介面公開給文字緩衝區。 如需詳細資訊，請參閱 [如何：使用舊版 API 註冊文字緩衝區事件](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)。 如果是 `IVsTextStreamEvents` 或 `IVsTextLinesEvents` 介面，變更會分別以一或兩個維度的座標傳回。  
  
## <a name="text-buffer-interfaces"></a>文字緩衝區介面  
 以下是文字緩衝區物件所執行的介面。  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|可以建立複合動作 (也就是在單一復原/重做單位中分組的動作) 。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|啟用由文字緩衝區所管理的檔資料的持續性。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|提供基本服務;由許多用戶端使用。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|使用二維座標提供讀取和寫入功能。 繼承自 `IVsTextBuffer`。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|提供快速、串流導向、連續存取緩衝區中的文字。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|提供使用一維座標的讀取和寫入功能。 繼承自 `IVsTextBuffer`。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|提供泛型屬性集合的存取。 最重要的屬性是緩衝區的名稱或標記。 您可以藉由建立 GUID 並使用它作為索引鍵，將您自己的亂數據儲存在緩衝區中，並使用此介面。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|支援事件的連接點。|  
  
## <a name="text-buffer-event-interfaces"></a>文字緩衝區事件介面  
 以下是文字緩衝區事件通知的介面。  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|當新的語言服務與文字緩衝區相關聯時，通知用戶端。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|當初始化文字緩衝區，以及對文字緩衝區中的資料進行變更時，通知用戶端。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|通知用戶端對一維座標中基礎文字緩衝區的變更。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|以二維座標通知用戶端變更基礎文字緩衝區。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|通知用戶端對使用者資料的變更。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|通知用戶端上一次認可手勢觸發事件，並提供變更的文字範圍。 `IVsPreliminaryTextChangeCommitEvents`回應復原或重做命令時，不會引發介面。 只有具有復原管理員的緩衝區才會引發事件。 `IVsPreliminaryTextChangeCommitEvents` 會在其他事件（例如整齊清單）之前引發，以確保其他事件不會在認可變更之前變更文字。 您的 VSPackage 必須監視 `IVsPreliminaryTextChangeCommitEvents` 介面或 `IVsFinalTextChangeCommitEvents` 介面，但不能同時監視兩者。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|通知用戶端上一次認可手勢觸發事件，並提供變更的文字範圍。 `IVsFinalTextChangeCommitEvents`回應復原或重做命令時，不會引發介面。 只有具有復原管理員的緩衝區才會引發事件。 `IVsFinalTextChangeCommitEvents` 僅供語言服務或可完全控制編輯的物件使用。 您的 VSPackage 必須監視 `IVsPreliminaryTextChangeCommitEvents` 介面或 `IVsFinalTextChangeCommitEvents` 介面，但不能同時監視兩者。|  
  
## <a name="see-also"></a>另請參閱  
 [使用舊版 API 存取文字緩衝區](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [如何：使用舊版 API 註冊文字緩衝區事件](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)
