---
title: VSTextBuffer 物件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5b68d443e542b6bd707aacc2b22d0efc1064152c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690647"
---
# <a name="vstextbuffer-object"></a>VSTextBuffer 物件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

文字緩衝區物件表示 Unicode 文字，也就是通常與檔案相關的資料流。 A<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>物件可以用核心編輯器中，內容之外，如果精靈是。  
  
 下表顯示的介面`VSTextBuffer`。  
  
|方法|描述|  
|------------|-----------------|  
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|標準的 OLE 介面。 主要用於處理緩衝區中的復原/取消復原。|  
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|標準的 OLE 介面。|  
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|標準的 OLE 介面。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|讓您能夠建立化合物動作 （也就是動作會分組放入單一復原/取消復原單位）。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|可讓受管理的文字緩衝的文件資料的持續性。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|提供基本的服務;許多用戶端使用。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|用來搜尋一個緩衝區。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|提供讀取和寫入功能使用二維座標。 繼承自 `IVsTextBuffer`。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|提供讀取和寫入使用一維座標的功能。 繼承自 `IVsTextBuffer`。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|提供快速、 在緩衝區中的文字資料流為導向的循序存取。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|提供存取權之屬性的泛型集合。 名稱或 moniker，緩衝區的最重要的屬性。 您可以儲存在緩衝區中，使用此介面的隨機資料，建立 GUID，並使用它做為索引鍵。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|支援的連接點事件。|  
  
## <a name="remarks"></a>備註  
 `VSTextBuffer`通常找到`QueryInterface`上呼叫`IVsTextBuffer`。 如需詳細資訊，請參閱 <<c0> [ 文字緩衝區](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [圖形編輯](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
