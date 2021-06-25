---
title: VSTextView 物件 |Microsoft Docs
description: VSTextView 物件是一個視窗，可讓使用者查看和編輯文字緩衝區的 Unicode 文字。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 90fad54be26c11db31d649d0ae6b25c108a6b361
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905159"
---
# <a name="vstextview-object"></a>VSTextView 物件

文字視圖是一個視窗，可讓使用者查看和編輯文字緩衝區的 Unicode 文字。 基本上，此視圖是大部分使用者作為編輯器的參考。 因為不同的文字圖層會將視圖與緩衝區分隔 (自動換行、將文字大綱，依此類推) ，所以不保證該視圖是緩衝區中文字的確切表示。 如需文字視圖的詳細資訊，請參閱 [使用舊版 API 存取文字 view](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-thetext-view-by-using-the-legacy-api?preserve-view=true&view=vs-2015)。

下表顯示物件中的介面 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> 。

|介面|描述|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|標準 OLE 介面。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|標準 OLE 介面。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|標準 OLE 介面。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|標準 OLE 介面。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|可以建立複合動作 (也就是在單一復原/重做單位中分組的動作) 。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|提供管理和存取視圖的基本方法。 `IVsTextView` 不是執行緒安全的。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|建立及管理視窗窗格。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|與文字圖層互動。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|從不同的執行緒在視圖上執行作業。|

## <a name="see-also"></a>另請參閱

- [編輯圖形](https://www.microsoft.com/download/details.aspx?id=55984)
- [VSTextBuffer 物件](../extensibility/vstextbuffer-object.md)