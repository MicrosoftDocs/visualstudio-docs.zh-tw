---
description: 抓取此程式已載入並正在執行的模組清單。
title: IDebugProgram2：： EnumModules |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumModules
helpviewer_keywords:
- IDebugProgram2::EnumModules
ms.assetid: 876ac9da-3b7c-4156-b79a-8f340e9fcea6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af640cf7e76da0e6cf7bb202cda08792c783e0d5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076026"
---
# <a name="idebugprogram2enummodules"></a>IDebugProgram2::EnumModules
抓取此程式已載入並正在執行的模組清單。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumModules( 
   IEnumDebugModules2** ppEnum
);
```

```csharp
int EnumModules( 
   out IEnumDebugModules2 ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\
擴展傳回包含模組清單的 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 模組是 DLL 或元件，通常會列在 [ **模組** ] 的 [偵錯工具] 視窗中。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
