---
title: UdtKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- UdtKind enumeration
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45ed43bf65c38890ca7ebda1a6b1719532697eae
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738451"
---
# <a name="udtkind"></a>UdtKind
描述各種不同的使用者定義型別（UDT）。

## <a name="syntax"></a>語法

```C++
enum UdtKind {
    UdtStruct,
    UdtClass,
    UdtUnion,
    UdtInterface
};
```

## <a name="elements"></a>項目
UdtStruct UDT 是一個結構。

UdtClass UDT 是一個類別。

UdtUnion UDT 是聯集。

UdtInterface UDT 是一個介面。

## <a name="remarks"></a>備註
此列舉中的值是由[IDiaSymbol：： get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)方法所傳回。

## <a name="requirements"></a>需求
標頭： cvconst。h

## <a name="see-also"></a>請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)
