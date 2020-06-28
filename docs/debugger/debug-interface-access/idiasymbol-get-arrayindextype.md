---
title: IDiaSymbol::get_arrayIndexType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 7bbe3bd3525abd5ac7fccbae66b603ce8d2a6dbf
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464307"
---
# <a name="idiasymbolget_arrayindextype"></a>IDiaSymbol::get_arrayIndexType
抓取符號之陣列索引類型的符號介面。

## <a name="syntax"></a>語法

```C++
HRESULT get_arrayIndexType ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回代表符號之陣列索引類型的[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示此屬性無法用於符號。

## <a name="remarks"></a>備註
 某些語言可以指定用來做為陣列索引的類型。 從這個方法傳回的符號會指定該型別。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v7.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)