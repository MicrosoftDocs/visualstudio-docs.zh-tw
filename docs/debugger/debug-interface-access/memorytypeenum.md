---
title: MemoryTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 2cd255ab59c9d46676ba46baddd9cee7e3ef4cc2
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461179"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
指定要存取的記憶體類型。

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
`MemTypeCode`只存取程式碼記憶體。

`MemTypeData`存取資料或堆疊記憶體。

`MemTypeStack`只存取堆疊記憶體。

`MemTypeAny`存取任何類型的記憶體。

## <a name="remarks"></a>備註
此列舉中的值會傳遞至[IDiaStackWalkHelper：： readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)方法，以限制存取不同類型的記憶體。

## <a name="requirements"></a>需求
標頭： cvconst。h

## <a name="see-also"></a>另請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
