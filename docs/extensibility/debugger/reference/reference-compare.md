---
title: REFERENCE_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- REFERENCE_COMPARE
helpviewer_keywords:
- REFERENCE_COMPARE enumeration
ms.assetid: e31cdc78-f621-498b-9ca4-aefa790b9f6f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b518e9bcfd77f489dd38a96eb8e378610841feb5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913461"
---
# <a name="referencecompare"></a>REFERENCE_COMPARE
指定參考的比較類型。

## <a name="syntax"></a>語法

```cpp
enum enum_REFERENCE_COMPARE { 
   REF_COMPARE_EQUAL        = 0x0001,
   REF_COMPARE_LESS_THAN    = 0x0002,
   REF_COMPARE_GREATER_THAN = 0x0003
};
typedef DWORD REFERENCE_COMPARE;
```

```csharp
public enum enum_REFERENCE_COMPARE { 
   REF_COMPARE_EQUAL        = 0x0001,
   REF_COMPARE_LESS_THAN    = 0x0002,
   REF_COMPARE_GREATER_THAN = 0x0003
};
```

## <a name="members"></a>成員
 REF_COMPARE_EQUAL 指定等於比較。

 REF_COMPARE_LESS_THAN 指定更少的比較。

 REF_COMPARE_GREATER_THAN 指定大於-比較。

## <a name="remarks"></a>備註
 作為引數[比較](../../../extensibility/debugger/reference/idebugreference2-compare.md)方法。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)