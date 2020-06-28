---
title: IDiaSymbol：： get_isCTypes |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2 interface
ms.assetid: 00c73cf9-2933-472e-bc1d-d041f4d7e412
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 264e8dfb784af75a8138aa1b606e0f4a926f8d65
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463446"
---
# <a name="idiasymbolget_isctypes"></a>IDiaSymbol::get_isCTypes
抓取表示符號檔是否包含 C 類型的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_isCTypes(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>參數
 `pFlag`

脫銷`TRUE`如果符號檔包含 C 類型，則傳回，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。

## <a name="remarks"></a>備註
 這個屬性可從 `SymTagExe` 符號類型（請參閱[Exe](../../debugger/debug-interface-access/exe.md)）取得。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v8.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Convert.exe](../../debugger/debug-interface-access/exe.md)