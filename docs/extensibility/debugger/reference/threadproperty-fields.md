---
title: THREADPROPERTY_FIELDS |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b31c43187d1136f7a194c42749c430de6cd064a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713404"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
指定要檢索的線程資訊。

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

## <a name="fields"></a>欄位
 `TPF_ID`\
 初始化/使用`dwThreadId`[THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)結構的欄位。

 `TPF_SUSPENDCOUNT`\
 初始化/使用`dwSuspendCount`S結構`THREADPROPERTIE`的欄位。

 `TPF_STATE`\
 初始化/使用`dwThreadState`S結構`THREADPROPERTIE`的欄位。

 `TPF_PRIORITY`\
 初始化/使用`bstrPriority`S結構`THREADPROPERTIE`的欄位。

 `TPF_NAME`\
 初始化/使用`bstrName`S結構`THREADPROPERTIE`的欄位。

 `TPF_LOCATION`\
 初始化/使用`bstrLocation`S結構`THREADPROPERTIE`的欄位。

 `TPF_ALLFIELDS`\
 指定所有欄位。

## <a name="remarks"></a>備註
 這些值作為參數傳遞給[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)方法,以指示要初始化[THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)結構的欄位。

 這些值還用於結構`dwFields`的成員`THREADPROPERTIES`中,以指示使用哪些欄位有效。

 這些旗標可以稍微`OR`結合 。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
