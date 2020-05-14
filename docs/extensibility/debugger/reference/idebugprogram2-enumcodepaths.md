---
title: IDebugProgram2::枚舉代碼路徑 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b99651811cedbdb8ec0eca5b766e6d75651dd5d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723028"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
檢索源檔中給定位置的代碼路徑清單。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumCodePaths( 
   LPCOLESTR            pszHint,
   IDebugCodeContext2*  pStart,
   IDebugStackFrame2*   pFrame,
   BOOL                 fSource,
   IEnumCodePaths2**    ppEnum,
   IDebugCodeContext2** ppSafety
);
```

```csharp
int EnumCodePaths( 
   string                 pszHint,
   IDebugCodeContext2     pStart,
   IDebugStackFrame2      pFrame,
   Int                    fSource,
   out IEnumCodePaths2    ppEnum,
   out IDebugCodeContext2 ppSafety
);
```

## <a name="parameters"></a>參數
`pszHint`\
[在]IDE 中的 **「源**」或「**拆解**」檢視中游標下方的單詞。

`pStart`\
[在]表示當前代碼上下文的[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件。

`pFrame`\
[在][IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)物件,表示與當前斷點關聯的堆疊幀。

`fSource`\
[在]非零`TRUE`( ) 如果位於 **「源」** 視圖中`FALSE`,則為零 (), 如果在 **「拆解」** 視圖中。

`ppEnum`\
[出]返回包含代碼路徑清單的[IEnumCodePath2](../../../extensibility/debugger/reference/ienumcodepaths2.md)物件。

`ppSafety`\
[出]返回一個[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件,表示要設置為斷點的其他代碼上下文,以防跳過所選代碼路徑。 例如,在短路布爾表達式的情況下,可能會發生這種情況。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 代碼路徑描述為在程式執行中到達當前點而調用的方法或函數的名稱。 代碼路徑清單表示調用堆疊。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
