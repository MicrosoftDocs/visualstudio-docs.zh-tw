---
title: MemoryTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e0f0973c0491cd65c2d03be785bb03b8c2f31df
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227416"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
指定要存取記憶體的類型。

## <a name="syntax"></a>語法

```C++
enum MemoryTypeEnum {
    MemTypeCode,
    MemTypeData,
    MemTypeStack,
    MemTypeAny = -1
};
```

#### <a name="parameters"></a>參數
`MemTypeCode`  
存取僅限程式碼的記憶體。

`MemTypeData`  
存取資料或堆疊記憶體。

`MemTypeStack`  
存取僅堆疊記憶體。

`MemTypeAny`  
存取任何種類的記憶體。

## <a name="remarks"></a>備註
這個列舉型別中的值會傳遞至[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)方法，以限制存取不同類型的記憶體。

## <a name="requirements"></a>需求
標頭： cvconst.h

## <a name="see-also"></a>請參閱
[列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
