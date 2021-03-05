---
description: 取得反組解碼資料流程的範圍。
title: IDebugDisassemblyStream2：： GetScope |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetScope
helpviewer_keywords:
- IDebugDisassemblyStream2::GetScope
ms.assetid: 71c6e632-642a-42d8-a995-77e4ac190a5b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8b112975649ec477a036826e3dc938ba756615c0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154453"
---
# <a name="idebugdisassemblystream2getscope"></a>IDebugDisassemblyStream2::GetScope
取得反組解碼資料流程的範圍。

## <a name="syntax"></a>語法

```cpp
HRESULT GetScope( 
   DISASSEMBLY_STREAM_SCOPE* pdwScope
);
```

```csharp
int GetScope( 
   out enum_ DISASSEMBLY_STREAM_SCOPE pdwScope
);
```

## <a name="parameters"></a>參數
`pdwScope`\
擴展傳回 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) 列舉中的值，這個值會描述這個反組解碼資料流程的範圍。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 例如，反組解碼的範圍可以是函數或整個模組。

## <a name="see-also"></a>另請參閱
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
