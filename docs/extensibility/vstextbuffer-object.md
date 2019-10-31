---
title: VSTextBuffer 物件 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1895efa9ef10e1e554b98844619507224f09126
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189021"
---
# <a name="vstextbuffer-object"></a>VSTextBuffer 物件
文字緩衝區物件代表 Unicode 文字的資料流程，通常與檔案相關聯。 您可以在 [核心編輯器] 的內容之外使用 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 物件，就像在 wizard 中一樣。

 下表顯示 `VSTextBuffer`的介面。

|方法|描述|
|------------|-----------------|
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|標準的 OLE 介面。 用於在緩衝區中進行復原/重做處理。|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|標準的 OLE 介面。|
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|標準的 OLE 介面。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|可讓您建立複合動作（也就是在單一復原/重做單位中分組的動作）。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|啟用由文本緩衝區所管理之檔資料的持續性。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|提供基本的服務;由許多用戶端使用。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|用來搜尋緩衝區。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|提供使用二維座標的讀取和寫入功能。 繼承自 `IVsTextBuffer`。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|提供使用一維座標的讀取和寫入功能。 繼承自 `IVsTextBuffer`。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|針對緩衝區中的文字提供快速、以資料流程為導向的順序存取。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|提供泛型屬性集合的存取權。 最重要的屬性是緩衝區的名稱（或名字標記）。 您可以藉由建立 GUID 並使用它做為索引鍵，在緩衝區中儲存您自己的亂數據。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|支援事件的連接點。|

## <a name="remarks"></a>備註
 `VSTextBuffer` 通常是透過 `IVsTextBuffer`上的 `QueryInterface` 呼叫來找到。 如需詳細資訊，請參閱[文字緩衝區](/visualstudio/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?view=vs-2015)。

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [圖形編輯](https://www.microsoft.com/download/details.aspx?id=55984)