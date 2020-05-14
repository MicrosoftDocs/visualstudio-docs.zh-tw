---
title: IDebugProgram2::獲取拆解流 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2160f963ad1f3f37291519ced30b8096e33a6116
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722857"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
獲取此程式或此程式的一部分的拆解流。

## <a name="syntax"></a>語法

```cpp
HRESULT GetDisassemblyStream( 
   DISASSEMBLY_STREAM_SCOPE   dwScope,
   IDebugCodeContext2*        pCodeContext,
   IDebugDisassemblyStream2** ppDisassemblyStream
);
```

```csharp
int GetDisassemblyStream( 
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,
   IDebugCodeContext2             pCodeContext,
   out IDebugDisassemblyStream2   ppDisassemblyStream
);
```

## <a name="parameters"></a>參數
`dwScope`\
[在]指定定義拆解流範圍[的DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)枚舉中的值。

`pCodeContext`\
[在][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件,表示啟動拆解流的位置。

`ppDisassemblyStream`\
[出]返回表示拆解[流的IDebugDisdisssstream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。 如果`E_DISASM_NOTSUPPORTED`此特定體系結構不支援拆解,則返回。

## <a name="remarks"></a>備註
 如果`dwScopes`參數[DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)具有`DSS_HUGE`DISASSEMBLY_STREAM_SCOPE 枚 舉集的標誌,則拆解應返回大量拆解指令,例如,對於整個檔或模組。 如果未設置`DSS_HUGE`標誌,則拆解應限制為一個小區域,通常是單個函數的區域。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
