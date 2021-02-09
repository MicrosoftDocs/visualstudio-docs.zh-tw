---
title: CV_access_e | Microsoft Docs
description: 取得 CV_access_e 列舉型) 別的相關資訊，其可指定 debug interface access SDK 中成員 (存取層級的可見度範圍。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 68dc8ca76e9250cd06009a990c0136912b0d31e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857374"
---
# <a name="cv_access_e"></a>CV_access_e
指定成員函式和變數的可視性範圍 (存取層級) 。

## <a name="syntax"></a>Syntax

```C++
typedef enum CV_access_e {
    CV_private   = 1,
    CV_protected = 2,
    CV_public    = 3
} CV_access_e;
```

## <a name="elements"></a>元素
CV_private 成員有私用存取權。

CV_protected 成員有受保護的存取權。

CV_public 成員具有公用存取權。

## <a name="remarks"></a>備註
此 `friend` 存取規範不包含在此，因為可以存取類別的私用和受保護專案的非成員函式通常會使用它。 使用 [IDiaSymbol：： get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) 方法來尋找具有 `SymTagFriend` 存取權的符號。

## <a name="requirements"></a>規格需求
標頭： cvconst。h

## <a name="see-also"></a>另請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
