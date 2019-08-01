---
title: FRAMEINFO |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eb6a4a9f7408e5bcd03da464bfbc8ade3fa39e7e
ms.sourcegitcommit: 5694c5236fa32ba7f5bc1236a853f725ec7557e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68681089"
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
從[FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)列舉中指定要填入哪些欄位的旗標組合。

`m_bstrFuncName`\
與堆疊框架相關聯的函數名稱。

`m_bstrReturnType`\
與堆疊框架相關聯的傳回型別。

`m_bstrArgs`\
與堆疊框架相關聯之函數的引數。

`m_bstrLanguage`\
函數的實作為語言。

`m_bstrModule`\
與堆疊框架相關聯的模組名稱。

`m_addrMin`\
實體堆疊位址的最小值。

`m_addrMAX`\
實體堆疊位址的最大值。

`m_pFrame`\
代表此堆疊框架的[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)物件。

`m_pModule`\
代表包含此堆疊框架之模組的[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)物件。

`m_fHasDebugInfo`\
如果指定的框架`TRUE`中存在 debug 資訊, 則為非零 ()。

`m_fStaleCode`\
如果堆疊框架與`TRUE`不再有效的程式碼相關聯, 則為非零 ()。

`m_fAnnotatedFrame`\
如果堆疊框架是`TRUE`由會話 debug manager (SDM) 所標注, 則為非零 ()。

## <a name="remarks"></a>備註
這個結構會傳遞至要填入的[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)方法。 這個結構也會包含在[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)介面所包含的清單中, 而後者則是從[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)方法的呼叫傳回。

## <a name="requirements"></a>需求
標頭: msdbg。h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
