---
title: THREADPROPERTIES |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a2eb7abf897cf4891f08228dd5f0c918f580a1ce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850657"
---
# <a name="threadproperties"></a>THREADPROPERTIES
描述執行緒的屬性。

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
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)列舉中的旗標組合，描述此結構中的哪些欄位有效。

 `dwThreadId`\
 執行緒識別碼。

 `dwSuspendCount`\
 執行緒暫停計數。

 `dwThreadState`\
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)列舉中的值，指出作業執行緒的狀態。

 `bstrPriority`\
 指定執行緒優先順序的字串;例如，「上述標準」、「一般」或「時間緊迫」。

 `bstName`\
 執行緒名稱。

 `bstrLocation`\
 執行緒位置 (通常是最上層堆疊框架) ，通常表示為執行目前暫停之方法的名稱。

## <a name="remarks"></a>備註
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)方法的呼叫會填入此結構。 傳回的資訊通常用於填入 [ **執行緒** ] 視窗。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
