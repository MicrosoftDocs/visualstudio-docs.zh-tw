---
title: IDiaSymbol：： get_isDataAligned |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isDataAligned method
ms.assetid: ddd11a41-6c00-4829-acf4-aa1ace8c21a7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00507b5d69f46657968407170d9633f1d84c8e4f
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463425"
---
# <a name="idiasymbolget_isdataaligned"></a>IDiaSymbol::get_isDataAligned
抓取指定使用者定義型別（UDT）是否已對齊某個特定記憶體界限的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_isDataAligned(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>參數
 `pFlag`

脫銷`TRUE`如果 UDT 已對齊某個記憶體界限，則會傳回，否則會傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。

## <a name="remarks"></a>備註
 這個屬性通常是在可執行檔使用非預設的資料對齊來編譯時設定。 例如，Microsoft c + + 編譯器可以使用命令列選項/Zp 來變更資料對齊， <em>#</em> 其中 *#* 是位元組值。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v8.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)