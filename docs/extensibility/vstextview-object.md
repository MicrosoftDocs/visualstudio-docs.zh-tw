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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 927bbee8bde62ff24396ea7b50e55e901b8cff06
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189015"
---
# <a name="vstextview-object"></a>VSTextView 物件

[文字] 視圖是一個視窗，可讓使用者查看和編輯文字緩衝區的 Unicode 文字。 基本上，這是大部分使用者稱為編輯器的參考。 由於此視圖會由不同的文字圖層（自動換行、大綱文字等等）與緩衝區隔開，因此不保證會在緩衝區中確切呈現文字。 如需文字視圖的詳細資訊，請參閱[使用舊版 API 存取文字 view](/visualstudio/extensibility/accessing-thetext-view-by-using-the-legacy-api?view=vs-2015)。

下表顯示 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> 物件中的介面。

|介面|描述|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|標準的 OLE 介面。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|標準的 OLE 介面。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|標準的 OLE 介面。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|標準的 OLE 介面。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|可讓您建立複合動作（也就是以單一復原/重做單位分組的動作）。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|提供管理和存取視圖的基本方法。 `IVsTextView` 不是執行緒安全的。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|建立和管理視窗窗格。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|與文字圖層互動。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|從不同的執行緒在視圖上執行作業。|

## <a name="see-also"></a>請參閱

- [圖形編輯](https://www.microsoft.com/download/details.aspx?id=55984)
- [VSTextBuffer 物件](../extensibility/vstextbuffer-object.md)