---
title: VSTextView 物件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5be89d01a668fd05e70e73e31ffaf3742317c272
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138723"
---
# <a name="vstextview-object"></a>VSTextView 物件
[文字] 檢視是可讓使用者檢視和編輯文字緩衝的 Unicode 文字的視窗。 基本上，檢視是大部分使用者參考的項目做為編輯器。 檢視從緩衝區分隔文字的各層 （自動換行、 大綱文字等等），因為不保證會確切的緩衝區中的文字檢視。 如需 [文字] 檢視的詳細資訊，請參閱[使用舊版 API 存取 theText 檢視](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 下表顯示中的介面<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>物件。  
  
|介面|描述|  
|---------------|-----------------|  
|[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)|標準 OLE 介面。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|標準 OLE 介面。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|標準 OLE 介面。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|標準 OLE 介面。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|讓您建立複合的動作 （也就是動作會分組在單一復原/取消復原單位）。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|提供基本的方法來管理和存取檢視。 `IVsTextView` 不是安全執行緒。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|建立及管理視窗窗格。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|與文字層的互動。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|從不同執行緒中執行檢視上的作業。|  
  
## <a name="see-also"></a>另請參閱  
 [編輯圖表](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [VSTextBuffer 物件](../extensibility/vstextbuffer-object.md)   
 [使用舊版 API 存取 theText 檢視](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)