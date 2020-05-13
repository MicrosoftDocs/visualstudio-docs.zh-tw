---
title: IDebug文檔位置偏移2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d967ec9cf406f7dae691c3f05eda514e0907c7e3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731608"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
將源檔中的位置表示為字元偏移量。

## <a name="syntax"></a>語法

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 由 IDE 實現,並由調試引擎使用。

## <a name="methods"></a>方法
 下表顯示的方法`IDebugDocumentPositionOffset2`。

|方法|描述|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|檢索當前文檔位置的範圍。|

## <a name="remarks"></a>備註
 這將返回與[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)相同`char`的資訊, 但從文件開頭的偏移量返回。 這呈現的文檔就像它存在於磁碟上一樣,即一維字元陣列,而不是通常返回的行和列資訊。

## <a name="requirements"></a>需求
 標題: Msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
