---
title: IDiaSectionContrib::get_initializedData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_initializedData method
ms.assetid: f5c108be-a0cc-408b-9590-b8d44361810c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6386fc6bb460f7e0947680a9776af7646f1bec14
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742640"
---
# <a name="idiasectioncontribget_initializeddata"></a>IDiaSectionContrib::get_initializedData
抓取表示區段是否包含已初始化資料的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_initializedData ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷如果區段包含已初始化的資料，則傳回 `TRUE`;否則，會傳回 `FALSE`。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 如果不支援此屬性，則傳回 `S_FALSE`。 否則會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)