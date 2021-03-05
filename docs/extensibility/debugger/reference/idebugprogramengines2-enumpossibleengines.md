---
description: 傳回所有可能的 debug 引擎的 Guid (DE) 可將此程式進行偵錯工具。
title: IDebugProgramEngines2：： EnumPossibleEngines |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5719728637f26ed61283578565470b39fc60455
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151580"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
傳回所有可能的 debug 引擎的 Guid (DE) 可將此程式進行偵錯工具。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumPossibleEngines( 
   DWORD  celtBuffer,
   GUID*  rgguidEngines,
   DWORD* pceltEngines
);
```

```csharp
int EnumPossibleEngines( 
   uint      celtBuffer,
   GUID[]    rgguidEngines,
   ref DWORD pceltEngines
);
```

## <a name="parameters"></a>參數
`celtBuffer`\
在要傳回的解除 Guid 數目。 這也會指定陣列的大小上限 `rgguidEngines` 。

`rgguidEngines`\
[in，out]要填入的 DE Guid 陣列。

`pceltEngines`\
擴展傳回傳回的實際已解除 Guid 數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 如果緩衝區不夠大，則會傳回 [c + +] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` 或 [c #] 0x8007007A。

## <a name="remarks"></a>備註
 若要判斷有多少引擎存在，請呼叫這個方法一次，並將 `celtBuffer` 參數設定為0，並將 `rgguidEngines` 參數設定為 null 值。 這會傳回 `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` c # ) 的 (0x8007007A，而參數會傳回所 `pceltEngines` 需的緩衝區大小。

## <a name="see-also"></a>另請參閱
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
