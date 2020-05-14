---
title: VSText緩衝區物件 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5ea44d2b22c96d49f334f2ea33f9db8d69b5eb0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697717"
---
# <a name="vstextbuffer-object"></a>VSTextBuffer 物件
文本緩衝區物件表示 Unicode 文本流,通常與檔關聯。 物件<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>可以在核心編輯器的上下文之外使用,如嚮導。

 下表顯示了`VSTextBuffer`的介面。

|方法|描述|
|------------|-----------------|
|[IOleCommand目標](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|標準 OLE 介面。 用於在緩衝區中撤銷/重做處理。|
|[IPersist 檔案](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|標準 OLE 介面。|
|[I堅持流](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|標準 OLE 介面。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|啟用創建複合操作(即,在單個撤銷/重做單元中分組的操作)。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|啟用由文本緩衝區管理的文件數據的持久性。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|提供基本服務;許多用戶端使用。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|用於搜索緩衝區。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|使用二維座標提供讀寫功能。 繼承自 `IVsTextBuffer`。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|使用一維座標提供讀寫功能。 繼承自 `IVsTextBuffer`。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|提供對緩衝區中文本的快速、面向流的順序訪問。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|提供對屬性的通用集合的訪問。 最重要的屬性是緩衝區的名稱或名稱。 通過創建 GUID 並將其用作密鑰,可以使用此介面將您自己的隨機數據存儲在緩衝區中。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|支援事件的連接點。|

## <a name="remarks"></a>備註
 `VSTextBuffer`通常透過`QueryInterface`呼叫`IVsTextBuffer`找到 。 有關詳細資訊,請參閱[文字緩衝區](/visualstudio/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?view=vs-2015)。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [數位編輯](https://www.microsoft.com/download/details.aspx?id=55984)
