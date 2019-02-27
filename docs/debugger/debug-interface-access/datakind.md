---
title: DataKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 21630bea3022769d18748190c2a2d24c0e519a3c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608486"
---
# <a name="datakind"></a>DataKind
指出特定資料值的範圍。

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

## <a name="elements"></a>項目
無法判斷 DataIsUnknown 資料符號。

DataIsLocal 資料項目是本機變數。

DataIsStaticLocal 資料項目是靜態區域變數。

DataIsParam 資料項目是型式參數。

DataIsObjectPtr 資料項目就是物件指標 (`this`)。

DataIsFileStatic 資料的項目是檔案範圍的變數。

DataIsGlobal 資料項目是全域變數。

DataIsMember 資料項目是物件成員變數。

DataIsStaticMember 資料項目是類別的靜態變數。

DataIsConstant 資料項目是常數值。

## <a name="remarks"></a>備註
傳回這個列舉型別中的值[idiasymbol:: Get_datakind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)方法。

## <a name="requirements"></a>需求
標頭： cvconst.h

## <a name="see-also"></a>請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
