---
title: IDiaInjectedSource：： get_source |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b389df8220766ffbdbf865a2b8e70877fe91b3f1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743342"
---
# <a name="idiainjectedsourceget_source"></a>IDiaInjectedSource::get_source
抓取原始程式碼位元組。

## <a name="syntax"></a>語法

```C++
HRESULT get_source ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>參數
 `cbData`

在代表資料緩衝區大小的位元組數目。

 `pcbData`

脫銷傳回位元組數目，表示傳回的位元組數。 如果 `NULL` `data`，則 `pcbData` 是可用的資料位元組總數。

 `data[]`

脫銷要填入來源位元組的緩衝區。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 如果不支援此屬性，則傳回 `S_FALSE`。 否則會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)