---
title: EXCEPTION_INFO |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a305d34123d02b1fdbd545a438db4461643ed185
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737027"
---
# <a name="exception_info"></a>EXCEPTION_INFO
描述正在調試的程式引發的異常或運行時錯誤。

## <a name="syntax"></a>語法

```cpp
typedef struct tagEXCEPTION_INFO {
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    BSTR            bstrExceptionName;
    DWORD           dwCode;
    EXCEPTION_STATE dwState;
    GUID            guidType;
} EXCEPTION_INFO;
```

```csharp
public struct EXCEPTION_INFO {
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public string         bstrExceptionName;
    public uint           dwCode;
    public uint           dwState;
    public Guid           guidType;
};
```

## <a name="members"></a>成員
`pProgram`\
[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件,表示發生異常的程式。

`bstrProgramName`\
發生異常的程式的名稱。

`bstrExceptionName`\
異常的名稱。

`dwCode`\
異常或運行時錯誤的標識代碼。

`dwState`\
定義異常狀態[EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)枚舉的值。

`guidType`\
GUID 語言識別碼(`guidLang``guidEng`或 "

## <a name="remarks"></a>備註
此結構作為參數傳遞給[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)和[RemoveSetexception](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)方法。 此結構也會傳遞到要填充的[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)方法。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
- [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)
