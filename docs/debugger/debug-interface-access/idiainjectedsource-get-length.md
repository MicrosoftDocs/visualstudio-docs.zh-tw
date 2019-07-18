---
title: 'Idiainjectedsource:: Get_length |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_length method
ms.assetid: 38b88b8b-c2e0-4b2d-8b8b-9ff373733e78
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8333c7e57c3cd3f240f8a72dd865e458b23bc299
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62828637"
---
# <a name="idiainjectedsourcegetlength"></a>IDiaInjectedSource::get_length
擷取的程式碼的位元組數目。

## <a name="syntax"></a>語法

```C++
HRESULT get_length ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]傳回程式碼的位元組的數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法所傳回的值是原始碼的長度和是相同的值，傳回[idiainjectedsource:: Get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)方法。

## <a name="see-also"></a>另請參閱
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
- [IDiaInjectedSource::get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)