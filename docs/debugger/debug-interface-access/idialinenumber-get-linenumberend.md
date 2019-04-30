---
title: IDiaLineNumber::get_lineNumberEnd | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_lineNumberEnd method
ms.assetid: b101853e-2bcf-47c1-acef-e13984c7ea9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb62d8588fdbf439508eed3e5b2cc81a840b9f3d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62828688"
---
# <a name="idialinenumbergetlinenumberend"></a>IDiaLineNumber::get_lineNumberEnd
擷取陳述式或運算式的結束位置的以一為基的來源行號。

## <a name="syntax"></a>語法

```C++
HRESULT get_lineNumberEnd ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]傳回陳述式或運算式的結束位置的行號。 如果值為零，則結尾資訊不存在。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)