---
title: EXCEPTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4c5863c9ebb790ebcbc267f62cc2a0a1fd14603c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686258"
---
# <a name="exceptioninfo"></a>EXCEPTION_INFO
描述例外狀況或擲回的正在偵錯之程式的執行階段錯誤。

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
pProgram [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件，表示的程式發生例外狀況。

bstrProgramName 程式的名稱中發生例外狀況。

bstrExceptionName 例外狀況的名稱。

dwCode 例外狀況或執行階段錯誤的識別程式碼。

dwState 的值從[EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)列舉型別，定義例外狀況的狀態。

guidType GUID 的語言識別項、 任一`guidLang`或`guidEng`。

## <a name="remarks"></a>備註
此結構會做為參數傳遞[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)並[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)方法。 此結構也會傳遞至[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)来填入的方法。

## <a name="requirements"></a>需求
標頭： msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
- [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)
