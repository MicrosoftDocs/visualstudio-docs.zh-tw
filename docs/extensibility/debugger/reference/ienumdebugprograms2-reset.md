---
title: IEnum調試程式2::重置 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Reset
helpviewer_keywords:
- IEnumDebugPrograms2::Reset
ms.assetid: b289242b-24ea-4df3-a811-20b0c8a903d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 68a1f33fa4512b29dc6da6927a60af382285a9ad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715617"
---
# <a name="ienumdebugprograms2reset"></a>IEnumDebugPrograms2::Reset
將枚舉重置為第一個元素。

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
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 呼叫此方法後,[對 Next](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)方法的下一個調用將返回枚舉的第一個元素。

## <a name="see-also"></a>另請參閱
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)
