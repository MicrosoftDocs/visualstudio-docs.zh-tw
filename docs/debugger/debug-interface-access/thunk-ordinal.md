---
description: 指定 Thunk 類型。
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8d9fe78eedd0166594daf43093aa525e3d8d3e88
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161589"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
指定 Thunk 類型。

## <a name="syntax"></a>Syntax

```C++
typedef enum THUNK_ORDINAL {
    THUNK_ORDINAL_NOTYPE,
    THUNK_ORDINAL_ADJUSTOR,
    THUNK_ORDINAL_VCALL,
    THUNK_ORDINAL_PCODE,
    THUNK_ORDINAL_LOAD

    // trampoline thunk ordinals - only for use in Trampoline thunk symbols
    THUNK_ORDINAL_TRAMP_INCREMENTAL,
    THUNK_ORDINAL_TRAMP_BRANCHISLAND,
} THUNK_ORDINAL;
```

## <a name="elements"></a>元素
THUNK_ORDINAL_NOTYPE 標準 Thunk。

THUNK_ORDINAL_ADJUSTOR `this` ADJUSTOR Thunk。

THUNK_ORDINAL_VCALL 虛擬呼叫 Thunk。

THUNK_ORDINAL_PCODE P-code Thunk。

THUNK_ORDINAL_LOAD 延遲載入 Thunk。

THUNK_ORDINAL_TRAMP_INCREMENTAL 累加 trampoline Thunk (trampoline Thunk 可用來將來自某個記憶體空間的呼叫彈跳至另一個) 。

THUNK_ORDINAL_TRAMP_BRANCHISLAND 的分支點 trampoline Thunk。

## <a name="remarks"></a>備註
此列舉中的值會從 [IDiaSymbol：： get_ThunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) 方法的呼叫傳回。

## <a name="requirements"></a>規格需求
標頭： cvconst。h

## <a name="see-also"></a>另請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
