---
title: IDebugdisassemblystream2::閱讀 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a4f5c0250405c2e2a0314b52c4cbc64d749fc0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732090"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
讀取從拆解流中的當前位置開始的指令。

## <a name="syntax"></a>語法

```cpp
HRESULT Read( 
   DWORD                     dwInstructions,
   DISASSEMBLY_STREAM_FIELDS dwFields,
   DWORD*                    pdwInstructionsRead,
   DisassemblyData*          prgDisassembly
);
```

```csharp
int Read( 
   uint                           dwInstructions,
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,
   out uint                       pdwInstructionsRead,
   DisassemblyData[]              prgDisassembly
);
```

## <a name="parameters"></a>參數
`dwInstructions`\
[在]要拆卸的說明數。 此值也是`prgDisassembly`數位的最大長度。

`dwFields`\
[在][DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)枚舉中的標誌的組合,指示要填寫`prgDisassembly`的 欄位。

`pdwInstructionsRead`\
[出]返回實際拆解的說明數。

`prgDisassembly`\
[出]一系列用拆解代碼填充[的拆解數據](../../../extensibility/debugger/reference/disassemblydata.md)結構,每個拆解指令一個結構。 此陣列的長度由`dwInstructions`參數決定。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 可透過調用[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)方法獲取當前作用網域中可用的最大指令數。

 可以通過調用[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)方法更改讀取下一個指令的當前位置。

 可以將`DSF_OPERANDS_SYMBOLS`標誌添加到參數中`DSF_OPERANDS`的標誌`dwFields`中,以指示在拆解指令時應使用符號名稱。

## <a name="see-also"></a>另請參閱
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
