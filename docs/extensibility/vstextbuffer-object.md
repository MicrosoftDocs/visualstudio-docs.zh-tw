---
title: "VSTextBuffer 物件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d25551d6af9b2250275713541dc9c9df39ca90ec
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="vstextbuffer-object"></a>VSTextBuffer 物件
文字緩衝區物件表示 Unicode 文字，通常與檔案相關聯的資料流。 A<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>物件可以用核心編輯器中，內容之外，如果精靈是。  
  
 下表顯示的介面`VSTextBuffer`。  
  
|方法|說明|  
|------------|-----------------|  
|[IOleCommandTarget](http://msdn.microsoft.com/library/windows/desktop/ms683797)|標準 OLE 介面。 主要用來處理在緩衝區中的復原/取消復原。|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|標準 OLE 介面。|  
|[IPersistStream](http://msdn.microsoft.com/library/windows/desktop/ms690091)|標準 OLE 介面。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|讓您建立組合動作 （也就是動作會分組在單一復原/取消復原單位）。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|可讓文字緩衝區所管理的文件資料的持續性。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|提供基本的服務。許多用戶端使用。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|用來搜尋一個緩衝區。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|提供讀取和寫入功能使用二維座標。 繼承自 `IVsTextBuffer`。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|提供讀取和寫入使用一維座標的功能。 繼承自 `IVsTextBuffer`。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|提供快速、 在緩衝區中的文字資料流為導向的循序存取。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|提供存取的屬性泛型集合。 名稱或 moniker 時，緩衝區的最重要的屬性。 您可以儲存在緩衝區中，使用此介面的隨機資料，建立 GUID，並使用它做為索引鍵。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|支援的連接點事件。|  
  
## <a name="remarks"></a>備註  
 `VSTextBuffer`通常所找到`QueryInterface`上呼叫`IVsTextBuffer`。 如需詳細資訊，請參閱[文字緩衝區](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [編輯圖表](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)