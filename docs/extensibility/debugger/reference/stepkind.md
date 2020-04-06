---
title: 步進 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- STEPKIND
helpviewer_keywords:
- STEPKIND enumeration
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7ed2877c880d3cd2674f62b4f900a6e923bb29d9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713563"
---
# <a name="stepkind"></a>STEPKIND
指定步進的步驟類型。

## <a name="syntax"></a>語法

```cpp
enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
typedef DWORD STEPKIND;
```

```csharp
public enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
```

## <a name="fields"></a>欄位
 `STEP_INTO`\
 步驟進入函數。

 `STEP_OVER`\
 在函數上執行步驟。

 `STEP_OUT`\
 退出函數。

 `STEP_BACKWARDS`\
 向後的步驟進入函數。

## <a name="remarks"></a>備註
 作為參數傳遞給[Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)方法。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [步驟](../../../extensibility/debugger/reference/idebugprocess3-step.md)
