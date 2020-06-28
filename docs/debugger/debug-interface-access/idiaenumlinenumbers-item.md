---
title: IDiaEnumLineNumbers::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Item method
ms.assetid: 08efbeaf-22f7-49e9-96a8-bb906dfe4fd8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1eae34788cfed9f509e979df8efae6657f330d5
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468214"
---
# <a name="idiaenumlinenumbersitem"></a>IDiaEnumLineNumbers::Item
透過索引來抓取行號。

## <a name="syntax"></a>語法

```C++
HRESULT Item ( 
   DWORD            index,
   IDiaLineNumber** lineNumber
);
```

#### <a name="parameters"></a>參數
 索引

在要抓取的[IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)物件索引。 索引的範圍是0到 `count` -1，其中 `count` 是由[IDiaEnumLineNumbers：： get_Count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md)方法所傳回。

 lineNumber

脫銷傳回[IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)物件，代表所需的行號。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)