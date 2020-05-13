---
title: 線程屬性 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd0ed4e33b1f8e0e905f3c88493c9f513c177fbc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713429"
---
# <a name="threadproperties"></a>THREADPROPERTIES
描述線程的屬性。

## <a name="syntax"></a>語法

```cpp
typedef struct _tagTHREADPROPERTIES { 
   THREADPROPERTY_FIELDS dwFields;
   DWORD                 dwThreadId;
   DWORD                 dwSuspendCount;
   DWORD                 dwThreadState;
   BSTR                  bstrPriority;
   BSTR                  bstrName;
   BSTR                  bstrLocation;
} THREADPROPERTIES;
```

```csharp
public struct THREADPROPERTIES { 
   public uint   dwFields;
   public uint   dwThreadId;
   public uint   dwSuspendCount;
   public uint   dwThreadState;
   public string bstrPriority;
   public string bstrName;
   public string bstrLocation;
};
```

## <a name="members"></a>成員
 `dwFields`\
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)枚舉中的標誌的組合,描述此結構中的哪些欄位有效。

 `dwThreadId`\
 線程識別碼。

 `dwSuspendCount`\
 線程掛起計數。

 `dwThreadState`\
 [來自 THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)枚舉的值,指示操作線程的狀態。

 `bstrPriority`\
 指定線程優先權的字串;字串例如,"高於正常"、"正常"或"時間關鍵"。

 `bstName`\
 線程名稱。

 `bstrLocation`\
 線程位置(通常是最頂層堆疊幀)通常表示為當前停止執行的方法的名稱。

## <a name="remarks"></a>備註
 此結構由對[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)方法的調用填充。 傳回的資訊通常用於填充 **「線程」** 視窗。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
