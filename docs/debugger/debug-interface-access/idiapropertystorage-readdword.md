---
title: IDiaPropertyStorage：： ReadDWORD |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadDWORD
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1764ec83a69dcc5daff267767594473bf690b341
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742901"
---
# <a name="idiapropertystoragereaddword"></a>IDiaPropertyStorage::ReadDWORD
讀取屬性集內的 `DWORD` 值。

## <a name="syntax"></a>語法

```C++
HRESULT ReadDWORD ( 
   PROPID id,
   DWORD* pValue
);
```

#### <a name="parameters"></a>參數
 `id`

在要讀取之屬性的識別碼（`PROPID` 在 Wtypes.h 中定義為 `ULONG`）。

 `pValue`

脫銷傳回屬性值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則會傳回錯誤碼。 如果屬性不是 `DWORD` 類型，則傳回 `E_INVALIDARG`。

## <a name="remarks"></a>備註
 @No__t_0 是由 Windows 定義為32位不帶正負號的整數。

## <a name="see-also"></a>請參閱
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)