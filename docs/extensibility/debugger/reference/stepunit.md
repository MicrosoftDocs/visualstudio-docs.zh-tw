---
title: STEPUNIT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- STEPUNIT
helpviewer_keywords:
- STEPUNIT enumeration
ms.assetid: cb8441f2-f744-4e73-acfe-ae8542df9649
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 803aafb60d7ada5b3339735fc0a10c66bb4925e0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329169"
---
# <a name="stepunit"></a>STEPUNIT
指定間距單位逐步執行。

## <a name="syntax"></a>語法

```cpp
enum enum_STEPUNIT { 
   STEP_STATEMENT   = 0,
   STEP_LINE        = 1,
   STEP_INSTRUCTION = 2
};
typedef DWORD STEPUNIT;
```

```csharp
enum enum_STEPUNIT { 
   STEP_STATEMENT   = 0,
   STEP_LINE        = 1,
   STEP_INSTRUCTION = 2
};
```

## <a name="fields"></a>欄位
 `STEP_STATEMENT`\
 陳述式的步驟。

 `STEP_LINE`\
 所列的步驟。

 `STEP_INSTRUCTION`\
 依指示的步驟。

## <a name="remarks"></a>備註
 作為引數[步驟](../../../extensibility/debugger/reference/idebugprocess3-step.md)方法。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)