---
title: 使用舊版 API 存取文字 View |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f9396e4523e38e7313efb5668c4680f551558ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184937"
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>使用舊版 API 存取文字檢視
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

文字視圖是儲存在文字緩衝區中的文字呈現。 您可以使用舊版 API 來存取文字視圖，如下一節所示。  
  
## <a name="text-view-object"></a>Text View 物件  
 每個視圖都與它自己的文字緩衝區相關聯，而 view 是緩衝區中資料的視窗。 下圖顯示以表示的 text view 物件的主要介面 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> 。  
  
 ![Visual Studio 文字檢視物件](../extensibility/media/vstextview.gif "vstextview")  
Text view 物件  
  
 此視圖是在緩衝區中呈現文字的方式。 它包含自動換行和大綱等功能，讓您在視圖中看到的內容不是緩衝區中文字的確切表示。  
  
 視圖可讓其他服務或進程攔截傳入的命令，並在其上對其採取動作，然後再對其採取動作。 最常見的服務就是語言服務。 例如，語言服務可能需要攔截 ENTER 鍵的命令，以提供自訂縮排行為或工具提示。  
  
## <a name="adding-functionality-to-the-text-view"></a>將功能加入至文字視圖  
 您可以藉由處理特定的按鍵來自訂文字視圖行為。 若要攔截按鍵，您可以 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> 在物件上執行，並提供命令目標 (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) 來監視和攔截命令。  
  
 文字視圖會使用命令篩選的順序架構。 藉由呼叫方法，將新的命令篩選 (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 物件) 新增至序列 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 。  
  
 使用介面可提供文字視圖的事件通知 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` 。 在您的用戶端物件上執行這個介面，以接收文字視圖變更的通知。 使用 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> 文字視圖上的介面來接收來自視圖之變更的通知，以將此介面公開到文字視圖。  
  
## <a name="see-also"></a>另請參閱  
 [使用舊版 API 變更視圖設定](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [使用文字管理員監視全域設定](../extensibility/using-the-text-manager-to-monitor-global-settings.md)
