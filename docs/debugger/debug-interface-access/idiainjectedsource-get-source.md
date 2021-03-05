---
description: 捕獲原始程式碼位元組。
title: IDiaInjectedSource：： get_source |Microsoft 檔
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
ms.openlocfilehash: 248fc00320f94b297a9b0697742dff6e3fbd2004
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148413"
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
