---
title: STEPKIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- STEPKIND
helpviewer_keywords:
- STEPKIND enumeration
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa9c1805c7eaba480cd46ebc6e73ee370e3cbb22
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460777"
---
# <a name="stepkind"></a>STEPKIND
指定用於逐步執行步驟種類。

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
 逐步執行函式。

 `STEP_OVER`\
 不是進入函式。

 `STEP_OUT`\
 跳離函式。

 `STEP_BACKWARDS`\
 向後逐步執行函式。

## <a name="remarks"></a>備註
 作為引數[步驟](../../../extensibility/debugger/reference/idebugprocess3-step.md)方法。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)