---
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 641687dbcfa6bf50ba9e848de589662d282d0c7b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62864569"
---
# <a name="threadpropertyfields"></a>THREADPROPERTY_FIELDS
指定要擷取執行緒的相關資訊。

## <a name="syntax"></a>語法

```cpp
enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
typedef DWORD THREADPROPERTY_FIELDS;
```

```csharp
public enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
```

## <a name="members"></a>成員
 初始化/使用 TPF_ID`dwThreadId`欄位[THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)結構。

 初始化/使用 TPF_SUSPENDCOUNT`dwSuspendCount`欄位`THREADPROPERTIE`S 結構。

 初始化/使用 TPF_STATE`dwThreadState`欄位`THREADPROPERTIE`S 結構。

 初始化/使用 TPF_PRIORITY`bstrPriority`欄位`THREADPROPERTIE`S 結構。

 初始化/使用 TPF_NAME`bstrName`欄位`THREADPROPERTIE`S 結構。

 初始化/使用 TPF_LOCATION`bstrLocation`欄位`THREADPROPERTIE`S 結構。

 TPF_ALLFIELDS 指定所有欄位。

## <a name="remarks"></a>備註
 這些值會傳遞做為引數[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)方法，以表示哪些欄位[THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)結構會進行初始化。

 這些值也會在`dwFields`隸屬`THREADPROPERTIES`表示哪些欄位已使用且有效的結構。

 這些旗標可能會結合的位元`OR`。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)