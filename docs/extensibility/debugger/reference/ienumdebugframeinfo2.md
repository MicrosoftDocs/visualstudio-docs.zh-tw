---
title: IEnumDebugFrameInfo2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0aa67792ced94afd9c4439cbc6ea577e6b85f28b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716618"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
此介面枚舉[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構。

## <a name="syntax"></a>語法

```
IEnumDebugFrameInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面,以提供描述當前調用堆疊的結構清單。

## <a name="notes-for-callers"></a>通話備註
 Visual Studio 呼叫[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)取得此介面,每當正在除錯的程式中出現斷點、異常或停止時。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IEnumDebugFrameInfo2`。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|檢索枚舉序列中指定數量的[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構。|
|[跳](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|在枚舉序列中跳過指定數量的[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構。|
|[重設](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|將枚舉序列重置為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|建立與當前枚舉器相同的枚舉狀態的枚舉器。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|獲取枚舉器中的[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構數。|

## <a name="remarks"></a>備註
 Visual Studio 獲取此介面是處理正在調試的程式上的斷點、異常或使用者生成的暫停的第一步。 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構清單表示當前調用堆疊,當前函數調用位於清單的開頭,最舊的函數調用位於清單的末尾。 每個`FRAMEINFO`表示一個堆疊幀,可以在其中計算表達式並查看局部變數。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
