---
title: GUID_ARRAY | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GUID_ARRAY structure
ms.assetid: 9e12500c-2c1c-49b1-a0ba-e08366c97eb8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3aa33d8cef230d07c9b5f7cd3bd11a538fa651a
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315517"
---
# <a name="guidarray"></a>GUID_ARRAY
描述可用的偵錯引擎的唯一識別碼的陣列。

## <a name="syntax"></a>語法

```cpp
typedef struct tagGUID_ARRAY
{
    DWORD dwCount;
    GUID *Members;
} GUID_ARRAY;
```

```csharp
public struct GUID_ARRAY
{
    public uint dwCount;
    public Guid Members;
}
```

## <a name="terms"></a>詞彙
dwCount  
陣列中的唯一識別項的數目。

成員  
包含唯一識別碼的陣列。

## <a name="remarks"></a>備註
此結構由[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)方法。

## <a name="requirements"></a>需求
標頭：Msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
[結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)  
[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)
