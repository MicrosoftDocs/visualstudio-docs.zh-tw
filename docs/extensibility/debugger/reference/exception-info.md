---
title: EXCEPTION_INFO |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3f6ecbd791297f4c186d22d9ed14c627cf7be43f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941849"
---
# <a name="exception_info"></a>EXCEPTION_INFO
描述正在進行調試的程式擲回的例外狀況或執行階段錯誤。

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
[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件，代表發生例外狀況的程式。

`bstrProgramName`\
發生例外狀況的程式名稱。

`bstrExceptionName`\
例外狀況的名稱。

`dwCode`\
例外狀況或執行階段錯誤的識別程式碼。

`dwState`\
[EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)列舉中的值，這個值會定義例外狀況的狀態。

`guidType`\
GUID 語言識別項， `guidLang` 也就是或 `guidEng` 。

## <a name="remarks"></a>備註
此結構會以參數形式傳遞至 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) 和 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) 方法。 此結構也會傳遞至要填入的 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) 方法。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
- [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)
