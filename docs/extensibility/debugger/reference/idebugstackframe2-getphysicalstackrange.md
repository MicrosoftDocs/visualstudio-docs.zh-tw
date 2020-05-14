---
title: IDebugStackFrame2::獲取物理堆疊範圍 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3df924c6c8a4373082d61575e4ad8a7ec3f161d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719665"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
獲取與堆疊幀關聯的物理地址範圍的與計算機相關的表示形式。

## <a name="syntax"></a>語法

```cpp
HRESULT GetPhysicalStackRange ( 
   UINT64* paddrMin,
   UINT64* paddrMax
);
```

```csharp
int GetPhysicalStackRange ( 
   out ulong paddrMin,
   out ulong paddrMax
);
```

## <a name="parameters"></a>參數
`paddrMin`\
[出]返回與此堆疊幀關聯的最低物理位址。

`paddrMax`\
[出]返回與此堆疊幀關聯的最高物理位址。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 此方法返回的信息由會話調試管理器 (SDM) 用於對堆疊幀進行排序。

 假定調用堆棧會向下擴展,也就是說,在記憶體地址越來越低時添加新堆棧幀。 運行時體系結構必須提供與此假設相匹配的物理堆疊範圍。

## <a name="see-also"></a>另請參閱
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
