---
title: THREADPROPERTIES |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55b3334c8bd28d3975f06aa39ca8c7fd719f1f9e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913349"
---
# <a name="threadproperties"></a>THREADPROPERTIES
描述執行緒屬性。

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
 dwFields A 中的旗標的組合[THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)列舉，描述在此結構中的哪一個欄位都有效。

 dwThreadId 執行緒 id。

 dwSuspendCount 執行緒暫停計數。

 dwThreadState 的值從[THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)列舉，指出作業的執行緒的狀態。

 bstrPriority 字串，指定的執行緒優先權。例如，"上方 Normal"、"Normal"或者 「 時間重大 」。

 bstName 執行緒名稱。

 bstrLocation 執行緒位置 （通常是最上層的堆疊框架），通常表示為目前停止執行方法的名稱。

## <a name="remarks"></a>備註
 此結構會填入藉由呼叫[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)方法。 因此傳回的資訊通常會用於填入**執行緒**視窗。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)