---
title: IDiaSectionContrib::get_comdat | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_comdat method
ms.assetid: 8bd9be8d-59ee-4698-b055-daba354b8dcc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef38d5c4afcb065f7a095501e2bf5d95ee493789
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742719"
---
# <a name="idiasectioncontribget_comdat"></a>IDiaSectionContrib::get_comdat
抓取表示區段是否為 COMDAT 記錄的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_comdat ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷如果區段是 COMDAT 記錄，則傳回 `TRUE`。否則，會傳回 `FALSE`。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 如果不支援此屬性，則傳回 `S_FALSE`。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 COMDAT 記錄是通用物件檔案格式（COFF）記錄，可讓連結器看到封裝的函式。

## <a name="see-also"></a>請參閱
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)