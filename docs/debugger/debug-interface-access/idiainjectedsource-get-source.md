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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8408145d83b3b78f8392603466980495ab32d24b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85467026"
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