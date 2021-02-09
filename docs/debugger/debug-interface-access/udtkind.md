---
title: UdtKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- UdtKind enumeration
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 44c543d09a360bfb7eadad11d7fca84764bb2006
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873391"
---
# <a name="udtkind"></a>UdtKind
描述 (UDT) 的各種使用者定義型別。

## <a name="syntax"></a>Syntax

```C++
enum UdtKind {
    UdtStruct,
    UdtClass,
    UdtUnion,
    UdtInterface
};
```

## <a name="elements"></a>元素
UdtStruct UDT 是一個結構。

UdtClass UDT 是一種類別。

UdtUnion UDT 是聯集。

UdtInterface UDT 是介面。

## <a name="remarks"></a>備註
[IDiaSymbol：： get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)方法會傳回這個列舉中的值。

## <a name="requirements"></a>規格需求
標頭： cvconst。h

## <a name="see-also"></a>另請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)
