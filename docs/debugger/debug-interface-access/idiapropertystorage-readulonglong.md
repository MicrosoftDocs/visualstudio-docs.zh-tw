---
title: IDiaPropertyStorage：： ReadULONGLONG |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadULONGLONG
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dde2f111e468b8ccf6c1d91440f06d3e7048a0f6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742857"
---
# <a name="idiapropertystoragereadulonglong"></a>IDiaPropertyStorage::ReadULONGLONG
讀取屬性集內的 `ULONGLONG` 值。

## <a name="syntax"></a>語法

```C++
HRESULT ReadULONGLONG ( 
   PROPID     id,
   ULONGLONG* pValue
);
```

#### <a name="parameters"></a>參數
 `id`

在要讀取之屬性的識別碼（`PROPID` 在 Wtypes.h 中定義為 `ULONG`）。

 `pValue`

脫銷傳回屬性值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則會傳回錯誤碼。 如果屬性不是 `ULONGLONG` 類型，則傳回 `E_INVALIDARG`。

## <a name="remarks"></a>備註
 @No__t_0 是由 Windows 定義為64位不帶正負號的整數。

## <a name="see-also"></a>請參閱
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)