---
title: FRAMEINFO |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e1d52989d5687e922e0cb0ab306efc5321ffecef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904755"
---
# <a name="frameinfo"></a>FRAMEINFO
描述堆疊框架。

## <a name="syntax"></a>語法

```cpp
typedef struct tagFRAMEINFO {
    FRAMEINFO_FLAGS    m_dwValidFields;
    BSTR               m_bstrFuncName;
    BSTR               m_bstrReturnType;
    BSTR               m_bstrArgs;
    BSTR               m_bstrLanguage;
    BSTR               m_bstrModule;
    UINT64             m_addrMin;
    UINT64             m_addrMax;
    IDebugStackFrame2* m_pFrame;
    IDebugModule2*     m_pModule;
    BOOL               m_fHasDebugInfo;
    BOOL               m_fStaleCode;
    BOOL               m_fAnnotatedFrame;
} FRAMEINFO;
```

```csharp
public struct FRAMEINFO {
    public uint              m_dwValidFields;
    public string            m_bstrFuncName;
    public string            m_bstrReturnType;
    public string            m_bstrArgs;
    public string            m_bstrLanguage;
    public string            m_bstrModule;
    public ulong             m_addrMin;
    public ulong             m_addrMax;
    public IDebugStackFrame2 m_pFrame;
    public IDebugModule2     m_pModule;
    public int               m_fHasDebugInfo;
    public int               m_fStaleCode;
    public int               m_fAnnotatedFrame;
} FRAMEINFO;
```

## <a name="members"></a>成員
`m_dwValidFields`\
[FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)列舉中的旗標組合，可指定要填入的欄位。

`m_bstrFuncName`\
與堆疊框架相關聯的函式名稱。

`m_bstrReturnType`\
與堆疊框架相關聯的傳回型別。

`m_bstrArgs`\
與堆疊框架相關聯之函數的引數。

`m_bstrLanguage`\
函數實作為的語言。

`m_bstrModule`\
與堆疊框架相關聯的模組名稱。

`m_addrMin`\
最小實體堆疊位址。

`m_addrMAX`\
最大實體堆疊位址。

`m_pFrame`\
代表這個堆疊框架的 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 物件。

`m_pModule`\
代表包含此堆疊框架之模組的 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 物件。

`m_fHasDebugInfo`\
`TRUE`如果指定的框架中有調試資訊，) 非零 (。

`m_fStaleCode`\
`TRUE`如果堆疊框架與不再有效的程式碼相關聯，則為非零 () 。

`m_fAnnotatedFrame`\
`TRUE`如果堆疊框架是以會話 debug manager (SDM) 進行批註，則) 非零 (。

## <a name="remarks"></a>備註
此結構會傳遞至要填入的 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) 方法。 此結構也會包含在 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) 介面中所包含的清單中，而此清單會從 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 方法的呼叫傳回。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
