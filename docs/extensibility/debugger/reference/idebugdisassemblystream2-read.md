---
title: IDebugDisassemblyStream2：： Read |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 720850096e7099ed95cbc5fa914bebb2bee580ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944663"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
從反組解碼資料流程中的目前位置開始讀取指示。

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
在要拆解的指令數目。 此值也是陣列的最大長度 `prgDisassembly` 。

`dwFields`\
在 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) 列舉中的旗標組合，表示要填寫的欄位 `prgDisassembly` 。

`pdwInstructionsRead`\
擴展傳回實際拆解的指令數目。

`prgDisassembly`\
擴展 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) 結構的陣列，這個陣列會填入拆解程式碼，每個拆解指令都有一個結構。 這個陣列的長度是由參數所決定 `dwInstructions` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 您可以藉由呼叫 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) 方法，取得目前範圍內可用的最大指令數目。

 您可以藉由呼叫 [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) 方法來變更從中讀取下一個指令的目前位置。

 `DSF_OPERANDS_SYMBOLS`旗標可以新增至 `DSF_OPERANDS` 參數中的旗 `dwFields` 標，以指出在反彙編指令時應使用符號名稱。

## <a name="see-also"></a>另請參閱
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
