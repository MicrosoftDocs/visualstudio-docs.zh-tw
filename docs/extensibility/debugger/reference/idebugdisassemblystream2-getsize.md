---
description: 取得此反組解碼資料流程的指示大小。
title: IDebugDisassemblyStream2：： GetSize |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetSize
helpviewer_keywords:
- IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94207c8e14306049068e838971aa778290de2ba6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154362"
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
取得此反組解碼資料流程的指示大小。

## <a name="syntax"></a>語法

```cpp
HRESULT GetSize( 
   UINT64* pnSize
);
```

```csharp
int GetSize( 
   out ulong pnSize
);
```

## <a name="parameters"></a>參數
`pnSize`\
擴展傳回指示中的大小。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 從這個方法傳回的值可以用來配置 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) 結構的陣列，然後傳遞給 [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [讀取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
