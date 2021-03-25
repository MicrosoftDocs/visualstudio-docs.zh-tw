---
description: 此結構是用來設定模組的 JustMyCode 資訊。
title: JMC_CODE_SPEC |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- JMC_CODE_SPEC
helpviewer_keywords:
- JMC_CODE_SPEC structure
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9bb05d55268d3f0ef497831616b8e27aae4bb86
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058075"
---
# <a name="jmc_code_spec"></a>JMC_CODE_SPEC
此結構是用來設定模組的 JustMyCode 資訊。

## <a name="syntax"></a>語法

```cpp
typedef struct _JMC_CODE_SPEC {
    BOOL fIsUserCode;
    BSTR bstrModuleName;
} JMC_CODE_SPEC;
```

```csharp
public struct JMC_CODE_SPEC {
    public int    fIsUserCode;
    public string bstrModuleName;
};
```

## <a name="members"></a>成員
`fIsUserCode`\
`TRUE`如果模組要視為使用者程式碼，則為非零 () ; 否則， `FALSE` 如果模組要視為外部程式碼而不是要進行調試，則為零 () 。

`bstrModuleName`\
有問題的模組名稱。

## <a name="remarks"></a>備註
此結構會以這類結構的清單傳遞給 [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md) 方法。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)
