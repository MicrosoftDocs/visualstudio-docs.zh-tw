---
title: CV_access_e | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bbe338ba9d3aa6cbc795606c3fa285526afdfd36
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745362"
---
# <a name="cv_access_e"></a>CV_access_e
指定成員函式和變數的可見度範圍（存取層級）。

## <a name="syntax"></a>語法

```C++
typedef enum CV_access_e {
    CV_private   = 1,
    CV_protected = 2,
    CV_public    = 3
} CV_access_e;
```

## <a name="elements"></a>項目
CV_private 成員具有私用存取權。

CV_protected 成員具有受保護的存取權。

CV_public 成員具有公用存取權。

## <a name="remarks"></a>備註
這裡不包含 `friend` 存取規範，因為它通常是由可存取類別的私用和受保護專案的非成員函式所使用。 使用[IDiaSymbol：： get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)方法來尋找具有 `SymTagFriend` 存取權的符號。

## <a name="requirements"></a>需求
標頭： cvconst。h

## <a name="see-also"></a>請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
