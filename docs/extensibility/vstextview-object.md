---
title: VSTextView 物件 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab54fce0271438f89ec66b4fc5d8db1ebe21634f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56721416"
---
# <a name="vstextview-object"></a>VSTextView 物件
文字檢視是一個可讓使用者檢視和編輯文字緩衝的 Unicode 文字的視窗。 基本上，檢視是大部分使用者做為編輯器的指。 因為檢視以各種文字層級 （自動換行、 大綱文字等等） 分隔的緩衝區，檢視不會保證是確切的緩衝區中的文字。 如需文字檢視的詳細資訊，請參閱[使用舊版 API 存取 theText 檢視](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)

 下表顯示中的介面<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>物件。

|介面|描述|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|標準的 OLE 介面。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|標準的 OLE 介面。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|標準的 OLE 介面。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|標準的 OLE 介面。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|讓您建立複合的動作 （也就是動作會分組放入單一復原/取消復原單位）。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|提供基本的方法來管理和存取檢視。 `IVsTextView` 不是限制執行緒安全。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|建立及管理視窗窗格。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|與文字層的互動。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|從不同的執行緒中執行檢視上的作業。|

## <a name="see-also"></a>另請參閱
- [圖形編輯](https://www.microsoft.com/download/details.aspx?id=55984)
- [VSTextBuffer 物件](../extensibility/vstextbuffer-object.md)
- [使用舊版 API 的存取 theText 檢視](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)