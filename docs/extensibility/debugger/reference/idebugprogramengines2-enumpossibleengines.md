---
title: IDebugProgram引擎2::枚舉可能引擎 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45916edbef4368c58f83426d6c73f3c692236cb9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722440"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
返回可以除錯此程式的所有可能的除錯引擎 (DE) 的 GUID。

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
[在]要返回的 DE GUID 的數量。 這還指定`rgguidEngines`數位的最大大小。

`rgguidEngines`\
[進出]要填寫的 DE GUID 陣列。

`pceltEngines`\
[出]返回返回的實際 DE GUID 數。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。 如果緩衝區不夠大`HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)`,則返回 [C++] 或 [C] 0x8007007A。

## <a name="remarks"></a>備註
 為了確定有多少引擎,使用`celtBuffer`參數設置為`rgguidEngines`0 和 參數設置為 null 值呼叫此方法一次。 這將返回`HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)`(0x8007007A 表示 C#),`pceltEngines`並且參數返回緩衝區的必要大小。

## <a name="see-also"></a>另請參閱
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
