---
description: 指定要抓取之執行緒的相關資訊。
title: THREADPROPERTY_FIELDS |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 698c803304cf5efd3375b6d49e4dedbc4622f4c1
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221830"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
指定要抓取之執行緒的相關資訊。

## <a name="syntax"></a>Syntax

```cpp
enum enum_THREADPROPERTY_FIELDS { 
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
public enum enum_THREADPROPERTY_FIELDS { 
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
 初始化/使用 `dwThreadId` [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) 結構的欄位。

 `TPF_SUSPENDCOUNT`\
 初始化/使用 `dwSuspendCount` S 結構的欄位 `THREADPROPERTIE` 。

 `TPF_STATE`\
 初始化/使用 `dwThreadState` S 結構的欄位 `THREADPROPERTIE` 。

 `TPF_PRIORITY`\
 初始化/使用 `bstrPriority` S 結構的欄位 `THREADPROPERTIE` 。

 `TPF_NAME`\
 初始化/使用 `bstrName` S 結構的欄位 `THREADPROPERTIE` 。

 `TPF_LOCATION`\
 初始化/使用 `bstrLocation` S 結構的欄位 `THREADPROPERTIE` 。

 `TPF_ALLFIELDS`\
 指定所有欄位。

## <a name="remarks"></a>備註
 這些值會以引數的形式傳遞至 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) 方法，以指出要初始化 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) 結構的哪些欄位。

 這些值也會用在 `dwFields` 結構的成員中， `THREADPROPERTIES` 以指出哪些欄位已使用且有效。

 這些旗標可以與位結合 `OR` 。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
