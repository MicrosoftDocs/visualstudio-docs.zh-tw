---
title: DataKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2423646976744da17d3e904246ac74f8b2e75f41
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468704"
---
# <a name="datakind"></a>DataKind
表示資料值的特定範圍。

## <a name="syntax"></a>語法

```C++
enum DataKind {
    DataIsUnknown,
    DataIsLocal,
    DataIsStaticLocal,
    DataIsParam,
    DataIsObjectPtr,
    DataIsFileStatic,
    DataIsGlobal,
    DataIsMember,
    DataIsStaticMember,
    DataIsConstant
};
```

## <a name="elements"></a>元素
無法判斷 DataIsUnknown 資料符號。

DataIsLocal 資料項目是一個區域變數。

DataIsStaticLocal 資料項目是靜態區域變數。

DataIsParam 資料項目是正式參數。

DataIsObjectPtr 資料項目是物件指標（ `this` ）。

DataIsFileStatic 資料項目是檔案範圍的變數。

DataIsGlobal 資料項目是一個全域變數。

DataIsMember 資料項目是物件成員變數。

DataIsStaticMember 資料項目是類別靜態變數。

DataIsConstant 資料項目是常數值。

## <a name="remarks"></a>備註
此列舉中的值是由[IDiaSymbol：： get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)方法所傳回。

## <a name="requirements"></a>需求
標頭： cvconst。h

## <a name="see-also"></a>另請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
