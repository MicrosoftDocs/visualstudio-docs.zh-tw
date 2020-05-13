---
title: REFERENCE_COMPARE |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- REFERENCE_COMPARE
helpviewer_keywords:
- REFERENCE_COMPARE enumeration
ms.assetid: e31cdc78-f621-498b-9ca4-aefa790b9f6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2aa9e7c608c4aabdbb808629112b922a5ed3322e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713724"
---
# <a name="reference_compare"></a>REFERENCE_COMPARE
指定引用的比較類型。

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

## <a name="fields"></a>欄位
 `REF_COMPARE_EQUAL`\
 指定相等的比較。

 `REF_COMPARE_LESS_THAN`\
 指定小於比較。

 `REF_COMPARE_GREATER_THAN`\
 指定大於比較。

## <a name="remarks"></a>備註
 作為參數傳遞給[比較](../../../extensibility/debugger/reference/idebugreference2-compare.md)方法。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [比較](../../../extensibility/debugger/reference/idebugreference2-compare.md)
