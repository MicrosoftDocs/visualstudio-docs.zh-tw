---
title: STEPUNIT |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- STEPUNIT
helpviewer_keywords:
- STEPUNIT enumeration
ms.assetid: cb8441f2-f744-4e73-acfe-ae8542df9649
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f42c6af308770132343e18b95a9f839717f6d401
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840089"
---
# <a name="stepunit"></a>STEPUNIT
指定逐步執行的步驟單位。

## <a name="syntax"></a>Syntax

```cpp
enum enum_STEPUNIT { 
   STEP_STATEMENT   = 0,
   STEP_LINE        = 1,
   STEP_INSTRUCTION = 2
};
typedef DWORD STEPUNIT;
```

```csharp
enum enum_STEPUNIT { 
   STEP_STATEMENT   = 0,
   STEP_LINE        = 1,
   STEP_INSTRUCTION = 2
};
```

## <a name="fields"></a>欄位
 `STEP_STATEMENT`\
 逐步執行語句。

 `STEP_LINE`\
 依行的步驟。

 `STEP_INSTRUCTION`\
 逐步指示。

## <a name="remarks"></a>備註
 以引數形式傳遞至 [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) 方法。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)
