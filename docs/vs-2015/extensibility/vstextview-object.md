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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690691"
---
# <a name="vstextview-object"></a>VSTextView 物件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

文字視圖是一種視窗，可讓使用者查看和編輯文字緩衝區的 Unicode 文字。 基本上，此視圖是大部分使用者作為編輯器的參考。 因為不同的文字圖層會將視圖與緩衝區分隔 (自動換行、將文字大綱，依此類推) ，所以不保證該視圖是緩衝區中文字的確切表示。 如需文字視圖的詳細資訊，請參閱 [使用舊版 API 存取文字 view](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 下表顯示物件中的介面 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> 。  
  
|介面|描述|  
|---------------|-----------------|  
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|標準 OLE 介面。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|標準 OLE 介面。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|標準 OLE 介面。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|標準 OLE 介面。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|可以建立複合動作 (也就是在單一復原/重做單位中分組的動作) 。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|提供管理和存取視圖的基本方法。 `IVsTextView` 不是安全線程。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|建立及管理視窗窗格。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|與文字圖層互動。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|從不同的執行緒在視圖上執行作業。|  
  
## <a name="see-also"></a>另請參閱  
 [編輯圖形](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [VSTextBuffer 物件](../extensibility/vstextbuffer-object.md)   
 [使用舊版 API 存取文字檢視](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
