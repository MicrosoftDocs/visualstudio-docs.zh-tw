---
title: IDebug文檔文本2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b5def7f6cc4ac5ced91ca0a273ce750003dca20
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731557"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
此介面表示文本文檔。

## <a name="syntax"></a>語法

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>實施者說明
 當需要提供原始碼時,調試引擎 (DE) 以文本形式實現此介面。 由於這是最典型的情況,如果 DE 實現[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面,它`IDebugDocumentText2`也應該實現該 介面。

## <a name="notes-for-callers"></a>通話備註
 使用`QueryInterface`方法從`IDebugDocument2`介面獲取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了介面上的方法外`IDebugDocument2`,此介面還實現以下方法:

|方法|描述|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|檢索文件中此位置的文字大小。|
|[取得文字](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|從文件中的指定位置檢索文本。|

## <a name="remarks"></a>備註
 實現此介面的物件還必須實現<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>介面,該介面<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>為[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)物件提供介面。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
