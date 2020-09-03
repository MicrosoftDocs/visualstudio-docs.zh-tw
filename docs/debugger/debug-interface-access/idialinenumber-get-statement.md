---
title: IDiaLineNumber：： get_statement |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_statement method
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ea4a05bfccddeedb29110ea6ee44f34f85534a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85466844"
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