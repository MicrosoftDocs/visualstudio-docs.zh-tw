---
description: 描述特定的電腦。
title: MACHINE_INFO |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO
helpviewer_keywords:
- MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8a4b9686e5e3eb565b3c7b1c86a90ceac45b37cc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082344"
---
# <a name="machine_info"></a>MACHINE_INFO
描述特定的電腦。

## <a name="syntax"></a>語法

```cpp
typedef struct tagMACHINE_INFO { 
   MACHINE_INFO_FIELDS Fields;
   BSTR                bstrName;
   MACHINE_INFO_FLAGS  Flags;
} MACHINE_INFO;
```

```csharp
public struct MACHINE_INFO { 
   public uint   Fields;
   public string bstrName;
   public uint   Flags;
};
```

## <a name="members"></a>成員
 `Fields`\
 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)列舉中的旗標組合，可指定要將結構的哪些欄位初始化。

 `bstrName`\
 電腦名稱。 相當於呼叫 [GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)。

 `Flags`\
 描述電腦屬性的 [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) 列舉中的旗標組合。

## <a name="remarks"></a>備註
 呼叫 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) 方法時，會傳回這個結構。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
