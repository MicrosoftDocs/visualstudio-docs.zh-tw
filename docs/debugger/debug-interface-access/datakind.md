---
description: 表示資料值的特定範圍。
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 24f13fc1157dd7f3de723474091a1f80e3717504
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151312"
---
# <a name="datakind"></a>DataKind
表示資料值的特定範圍。

## <a name="syntax"></a>Syntax

```C++
enum DataKind {
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

DataIsLocal 資料項目是本機變數。

DataIsStaticLocal 資料項目是靜態區域變數。

DataIsParam 資料項目是正式參數。

DataIsObjectPtr 資料項目是 () 的物件指標 `this` 。

DataIsFileStatic 資料項目是檔案範圍變數。

DataIsGlobal 資料項目是全域變數。

DataIsMember 資料項目是物件成員變數。

DataIsStaticMember 資料項目是類別靜態變數。

DataIsConstant 資料項目是常數值。

## <a name="remarks"></a>備註
[IDiaSymbol：： get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)方法會傳回這個列舉中的值。

## <a name="requirements"></a>規格需求
標頭： cvconst。h

## <a name="see-also"></a>另請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
