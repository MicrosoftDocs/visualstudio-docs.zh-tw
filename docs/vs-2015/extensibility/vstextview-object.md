---
title: VSTextView 物件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22e4d4cdf1e5ca610dbdb067f8195fb730139c3d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690691"
---
# <a name="vstextview-object"></a>VSTextView 物件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

文字檢視是一個可讓使用者檢視和編輯文字緩衝的 Unicode 文字的視窗。 基本上，檢視是大部分使用者做為編輯器的指。 因為檢視以各種文字層級 （自動換行、 大綱文字等等） 分隔的緩衝區，檢視不會保證是確切的緩衝區中的文字。 如需文字檢視的詳細資訊，請參閱[使用舊版 API 存取 theText 檢視](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 下表顯示中的介面<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>物件。  
  
|介面|描述|  
|---------------|-----------------|  
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|標準的 OLE 介面。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|標準的 OLE 介面。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|標準的 OLE 介面。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|標準的 OLE 介面。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|讓您建立複合的動作 （也就是動作會分組放入單一復原/取消復原單位）。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|提供基本的方法來管理和存取檢視。 `IVsTextView` 不是安全執行緒。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|建立及管理視窗窗格。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|與文字層的互動。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|從不同的執行緒中執行檢視上的作業。|  
  
## <a name="see-also"></a>另請參閱  
 [圖形編輯](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [VSTextBuffer 物件](../extensibility/vstextbuffer-object.md)   
 [使用舊版 API 存取文字檢視](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
