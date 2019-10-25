---
title: THREADSTATE |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d86baeeab046a7e605979d3af2d6329998f796ba
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727502"
---
# <a name="threadstate"></a>THREADSTATE
指定執行緒的狀態。

## <a name="syntax"></a>語法

```cpp
enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
typedef DWORD THREADSTATE;
```

```csharp
public enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
```

## <a name="fields"></a>欄位
 `THREADSTATE_RUNNING`\
 表示執行緒正在執行。

 `THREADSTATE_STOPPED`\
 表示執行緒因為中斷點而停止。

 `THREADSTATE_FRESH`\
 表示執行緒已建立，但尚未執行程式碼。

 `THREADSTATE_DEAD`\
 表示執行緒已失效。

 `THREADSTATE_FROZEN`\
 表示執行緒已凍結（無法執行任何執行）。

## <a name="remarks"></a>備註
 用於[THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)結構的 `dwThreadState` 欄位。

## <a name="requirements"></a>需求
 標頭： msdbg。h

 命名空間： VisualStudio。 Interop

 元件： VisualStudio. Interop .dll

## <a name="see-also"></a>請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)