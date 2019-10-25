---
title: IDiaLineNumber::get_columnNumber | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumber method
ms.assetid: e317f29a-6525-46a7-8421-33985392f8fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ac6eea93daf9b0ef7d8169a4f765c249f3b9ee4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743253"
---
# <a name="idialinenumberget_columnnumber"></a>IDiaLineNumber::get_columnNumber
抓取運算式或語句開始處的資料行編號。

## <a name="syntax"></a>語法

```cpp
HRESULT get_columnNumber ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回運算式或語句開始的資料行編號。 如果值為零，則不存在資料行資訊。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 如果不支援此屬性，則傳回 `S_FALSE`。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法所傳回的資料行值是行上語句第一個字元的那一行的位元組位移。

## <a name="see-also"></a>請參閱
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)