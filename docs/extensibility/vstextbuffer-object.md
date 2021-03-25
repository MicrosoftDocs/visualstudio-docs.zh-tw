---
title: VSTextBuffer 物件 |Microsoft Docs
description: VSTextBuffer 物件代表 Unicode 文字的資料流程，通常與檔案相關聯。 本文列出 VSTextBuffer 的介面。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a72491b118e0a51454181734a8fe388c2f7e851e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062183"
---
# <a name="vstextbuffer-object"></a>VSTextBuffer 物件
文字緩衝區物件代表 Unicode 文字的資料流程，通常與檔案相關聯。 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>物件可以在核心編輯器的內容之外使用，如同在中的 wizard。

 下表顯示的介面 `VSTextBuffer` 。

|方法|描述|
|------------|-----------------|
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|標準 OLE 介面。 用於緩衝區中的復原/重做處理。|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|標準 OLE 介面。|
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|標準 OLE 介面。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|可以建立複合動作 (也就是在單一復原/重做單位中分組的動作) 。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|啟用由文字緩衝區所管理的檔資料的持續性。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|提供基本服務;由許多用戶端使用。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|用來搜尋緩衝區。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|使用二維座標提供讀取和寫入功能。 繼承自 `IVsTextBuffer`。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|提供使用一維座標的讀取和寫入功能。 繼承自 `IVsTextBuffer`。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|提供快速、串流導向、連續存取緩衝區中的文字。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|提供泛型屬性集合的存取。 最重要的屬性是緩衝區的名稱或標記。 您可以藉由建立 GUID 並使用它作為索引鍵，將您自己的亂數據儲存在緩衝區中，並使用此介面。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|支援事件的連接點。|

## <a name="remarks"></a>備註
 `VSTextBuffer`通常是透過呼叫來找到 `QueryInterface` `IVsTextBuffer` 。 如需詳細資訊，請參閱 [文字緩衝區](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?preserve-view=true&view=vs-2015)。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [編輯圖形](https://www.microsoft.com/download/details.aspx?id=55984)