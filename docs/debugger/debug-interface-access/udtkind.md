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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 746ff69de6f58f85d16982522c6ac13dcbf4ce6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460969"
---
# <a name="udtkind"></a>UdtKind
描述 (UDT) 的各種使用者定義型別。

## <a name="syntax"></a>語法

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

## <a name="requirements"></a>需求
標頭： cvconst。h

## <a name="see-also"></a>另請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)
