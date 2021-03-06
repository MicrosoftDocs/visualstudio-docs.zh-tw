---
description: 以索引的方式抓取行號。
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6eeea52f2152d1674710d7c5ee2b5970a8cd91cd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157977"
---
# <a name="idiaenumlinenumbersitem"></a>IDiaEnumLineNumbers::Item
以索引的方式抓取行號。

## <a name="syntax"></a>語法

```C++
HRESULT Item ( 
   DWORD            index,
   IDiaLineNumber** lineNumber
);
```

#### <a name="parameters"></a>參數
 索引

在要抓取之 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) 物件的索引。 索引位於0到-1 的範圍內 `count` ，其中 `count` 是 [IDiaEnumLineNumbers：： get_Count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md) 方法所傳回的。

 lineNumber

擴展傳回代表所需行號的 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
