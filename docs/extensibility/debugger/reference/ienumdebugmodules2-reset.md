---
title: IEnumDebugModules2：： Reset |Microsoft Docs
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
ms.openlocfilehash: fdc98e9ac2d545670fde240cea914be9108b8f0f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956252"
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
