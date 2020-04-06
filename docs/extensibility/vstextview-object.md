---
title: VSTextView 物件 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81d5e02d6ec18f8561a83b414532a4b78def5c09
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697705"
---
# <a name="vstextview-object"></a>VSTextView 物件

文字檢視是一個視窗,允許使用者查看和編輯文本緩衝區的 Unicode 文字。 從本質上講,視圖是大多數使用者所說的編輯器。 由於檢視由各種文本圖層(換行、大綱文本等)與緩衝區分開,因此不能保證視圖是緩衝區中文本的精確表示形式。 關於文字檢視的詳細資訊,請參考[使用舊 API 存取文字檢視](/visualstudio/extensibility/accessing-thetext-view-by-using-the-legacy-api?view=vs-2015)。

下表顯示了物件中的<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>介面。

|介面|描述|
|---------------|-----------------|
|[IDrop來源](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|標準 OLE 介面。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|標準 OLE 介面。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|標準 OLE 介面。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|標準 OLE 介面。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|啟用複合操作(即分組在單個撤銷/重做單元中的操作)。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|提供管理和訪問視圖的基本方法。 `IVsTextView`不螺紋安全。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|建立和管理視窗窗格。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|與文字圖層互動。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|從其他線程對視圖執行操作。|

## <a name="see-also"></a>另請參閱

- [數位編輯](https://www.microsoft.com/download/details.aspx?id=55984)
- [VSTextBuffer 物件](../extensibility/vstextbuffer-object.md)
