---
description: 將模組列舉重設為第一個元素。
title: IEnumDebugModules2：： Reset |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Reset
helpviewer_keywords:
- IEnumDebugModules2::Reset
ms.assetid: f6ff364c-2644-4919-b950-3cb82eb6f601
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a395a31b029b0d6a63eda670b10cbe8d4132b5b2
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224716"
---
# <a name="ienumdebugmodules2reset"></a>IEnumDebugModules2::Reset
將列舉重設為第一個元素。

## <a name="syntax"></a>語法

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 呼叫這個方法之後，下一次呼叫 [next](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) 方法會傳回列舉的第一個元素。

## <a name="see-also"></a>另請參閱
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
