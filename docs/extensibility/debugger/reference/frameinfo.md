---
title: 框架資訊 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c40361a9739bf468de2038df4325fa1ac98337c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736791"
---
# <a name="frameinfo"></a>FRAMEINFO
描述堆疊幀。

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
[FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)枚舉中的標誌的組合,用於指定填充哪些欄位。

`m_bstrFuncName`\
與堆疊幀關聯的函數名稱。

`m_bstrReturnType`\
與堆疊幀關聯的返回類型。

`m_bstrArgs`\
與堆疊幀關聯的函數的參數。

`m_bstrLanguage`\
實現函數的語言。

`m_bstrModule`\
與堆疊幀關聯的模組名稱。

`m_addrMin`\
最小物理堆疊位址。

`m_addrMAX`\
最大物理堆疊位址。

`m_pFrame`\
表示此堆疊幀的[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)物件。

`m_pModule`\
[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)物件,表示包含此堆疊幀的模組。

`m_fHasDebugInfo`\
如果給定幀中`TRUE`存在調試資訊,則非零 ( )。

`m_fStaleCode`\
如果堆疊幀`TRUE`與不再有效的代碼相關聯,則非零 ( )。

`m_fAnnotatedFrame`\
如果堆疊幀`TRUE`由會話調試管理器 (SDM) 進行指示,則非零 ( )。

## <a name="remarks"></a>備註
此結構傳遞給要填充的[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)方法。 此結構還包含在[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)介面中包含的清單中,該清單又從調用[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)方法返回。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
