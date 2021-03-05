---
description: 抓取這個執行緒的堆疊框架清單。
title: IDebugThread2：： EnumFrameInfo |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c9ad740de00338596de622cbce1028768ddda638
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149336"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
抓取這個執行緒的堆疊框架清單。

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
在 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) 列舉中的旗標組合，可指定要填寫 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 結構的哪些欄位。指定將 `FIF_FUNCNAME_FORMAT` 函數名稱格式化為單一字串的旗標。

`nRadix`\
在用來格式化列舉值中數值資訊的基數。

`ppEnum`\
擴展傳回 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) 物件，其中包含描述堆疊框架的 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 結構清單。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 執行緒的框架會依序列舉，並先列舉目前的框架，並最後列舉最舊的框架。

## <a name="see-also"></a>另請參閱
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
