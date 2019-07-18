---
title: IDiaSymbol::get_arrayIndexType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_arrayIndexType method
ms.assetid: cd63b9ec-9694-406c-b37f-bde6bd5fcbf2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a89afb7eb7d16f95ab5212d8cc081ac1cd84521
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "64813947"
---
# <a name="idiasymbolgetarrayindextype"></a>IDiaSymbol::get_arrayIndexType
擷取之型別的陣列索引符號的符號介面。

## <a name="syntax"></a>語法

```C++
HRESULT get_arrayIndexType ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，表示符號的陣列索引型別。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

> [!NOTE]
> 傳回值為`S_FALSE`表示此屬性不適用於符號。

## <a name="remarks"></a>備註
 某些語言，可以指定為陣列的索引所使用的類型。 從這個方法傳回的符號指定該型別。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2.h|
|版本:|DIA SDK v7.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)