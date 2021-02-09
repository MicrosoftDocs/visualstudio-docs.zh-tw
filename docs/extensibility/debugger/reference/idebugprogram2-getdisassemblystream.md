---
title: IDebugProgram2：： GetDisassemblyStream |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e499d7b655cb79873b1cd3ef2954f054bba84f60
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844693"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
取得此程式的反組解碼資料流程或此程式的一部分。

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
在指定 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) 列舉中的值，這個值會定義反組解碼資料流程的範圍。

`pCodeContext`\
在代表開始反組解碼資料流程之位置的 [IDebugCodeCoNtext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 物件。

`ppDisassemblyStream`\
擴展傳回代表反組解碼資料流程的 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 `E_DISASM_NOTSUPPORTED`如果此特定架構不支援反組解碼，則會傳回。

## <a name="remarks"></a>備註
 如果 `dwScopes` 參數具有 `DSS_HUGE` [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) 列舉集合的旗標，則反組解碼應該會傳回大量的反組解碼指令，例如，針對整個檔案或模組。 如果 `DSS_HUGE` 未設定旗標，則應該將反組解碼限制為小型區域，通常是單一函式。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
