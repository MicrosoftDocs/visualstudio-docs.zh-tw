---
description: 描述方法或函式呼叫。
title: CODE_PATH |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CODE_PATH
helpviewer_keywords:
- CODE_PATH structure
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3b3e061fa0a9d6eb508e3085832007712cb6e434
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096508"
---
# <a name="code_path"></a>CODE_PATH
描述方法或函式呼叫。

## <a name="syntax"></a>語法

```cpp
typedef struct tagCODE_PATH { 
    BSTR                bstrName;
    IDebugCodeContext2* pCode;
} CODE_PATH;
```

```csharp
public struct CODE_PATH {
    public string            bstrName;
    public IDebugCodeContext pCode;
}
```

## <a name="members"></a>成員
`bstrName`\
程式碼路徑的名稱。

`pCode`\
[IDebugCodeCoNtext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件，可識別程式碼中要逐步執行函式的位置。

## <a name="remarks"></a>備註
此結構是用來將逐步執行至函式。 [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) 會從正在進行調試的程式中，傳回目前位置的所有呼叫。 此結構代表一種這類呼叫。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)
