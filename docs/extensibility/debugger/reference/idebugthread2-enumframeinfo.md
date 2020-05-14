---
title: IDebugThread2::枚舉資訊 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8bd3c6d46a577930cc7a2b87c85cd82a55f8cf66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718855"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
檢索此線程的堆疊幀的清單。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumFrameInfo ( 
   FRAMEINFO_FLAGS        dwFieldSpec,
   UINT                   nRadix,
   IEnumDebugFrameInfo2** ppEnum
);
```

```csharp
int EnumFrameInfo ( 
   enum_FRAMEINFO_FLAGS     dwFieldSpec,
   uint                     nRadix,
   out IEnumDebugFrameInfo2 ppEnum
);
```

## <a name="parameters"></a>參數
`dwFieldSpec`\
[在][FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)枚舉中的標誌的組合,指定要填充[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構的欄位。指定標誌`FIF_FUNCNAME_FORMAT`以將函數名稱格式化為單個字串。

`nRadix`\
[在]用於格式化枚舉器中的數位資訊的 Radix。

`ppEnum`\
[出]返回[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)物件,該物件包含描述堆疊幀的[FRAME 資訊](../../../extensibility/debugger/reference/frameinfo.md)結構清單。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 線程的幀按順序枚舉,當前幀首先枚舉,最舊幀最後枚舉。

## <a name="see-also"></a>另請參閱
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
