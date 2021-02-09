---
title: IDiaInjectedSource：： get_source |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2f44f30b063a34a0d5d5549cd1923b66c1dde9cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864863"
---
# <a name="idiainjectedsourceget_source"></a>IDiaInjectedSource::get_source
捕獲原始程式碼位元組。

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

擴展傳回代表傳回位元組的位元組數目。 如果 `data` 為 `NULL` ，則 `pcbData` 為可用的資料位元組總數。

 `data[]`

擴展要填入來源位元組的緩衝區。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援這個屬性，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)