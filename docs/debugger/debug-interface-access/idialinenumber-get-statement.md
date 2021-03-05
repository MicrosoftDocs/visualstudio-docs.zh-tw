---
description: 抓取旗標，指出這行資訊描述程式來源中語句的開頭，而不是運算式。
title: IDiaLineNumber：： get_statement |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_statement method
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e6c36852f5aa48bcd5146419415dd06ec9d0a847
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157438"
---
# <a name="idialinenumberget_statement"></a>IDiaLineNumber::get_statement
抓取旗標，指出這行資訊描述程式來源中語句的開頭，而不是運算式。

## <a name="syntax"></a>語法

```C++
HRESULT get_statement ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展 `TRUE` 如果這行資訊描述程式來源中語句的開頭，則傳回。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援這個屬性，則傳回。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 語句可以跨多行。 這個方法會指出相關行號是否標記這類多行語句的開頭。

## <a name="see-also"></a>另請參閱
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
