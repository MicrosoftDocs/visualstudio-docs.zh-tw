---
title: LAUNCH_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- LAUNCH_FLAGS
helpviewer_keywords:
- LAUNCH_FLAGS enumeration
ms.assetid: f51aab02-d257-4302-bb79-b7d8ba9ac4e5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d793adfd8be2fb86f51e94cfd43e8dbcbd75036f
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2019
ms.locfileid: "56449992"
---
# <a name="launchflags"></a>LAUNCH_FLAGS
指定偵錯啟動旗標。

## <a name="syntax"></a>語法

```cpp
enum enum_LAUNCH_FLAGS {
    LAUNCH_DEBUG      = 0x0000,
    LAUNCH_NODEBUG    = 0x0001,
    LAUNCH_ENABLE_ENC = 0x0002,
    LAUNCH_MERGE_ENV  = 0x0004
};
typedef DWORD LAUNCH_FLAGS;
```

```csharp
public enum enum_LAUNCH_FLAGS {
    LAUNCH_DEBUG      = 0x0000,
    LAUNCH_NODEBUG    = 0x0001,
    LAUNCH_ENABLE_ENC = 0x0002,
    LAUNCH_MERGE_ENV  = 0x0004
};
```

## <a name="members"></a>成員
LAUNCH_DEBUG  
啟動偵錯的處理程序。

LAUNCH_NODEBUG  
啟動程序，但不偵錯它。

LAUNCH_ENABLE_ENC  
已被取代，請勿使用。

LAUNCH_MERGE_ENV  
啟動處理程序，並將合併啟動的主控件的環境。

## <a name="remarks"></a>備註
這些值會傳遞做為引數[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)方法。

這些旗標可能會結合的位元`OR`。

## <a name="requirements"></a>需求
標頭： msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
[列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
