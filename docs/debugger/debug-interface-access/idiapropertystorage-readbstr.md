---
title: IDiaPropertyStorage：： ReadBSTR |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBSTR
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef0b5bac11a1bf3da7e8081f7ae24b6a7a6f1a71
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742922"
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
讀取屬性集內的 `BSTR` 值。

## <a name="syntax"></a>語法

```C++
HRESULT ReadBSTR ( 
   PROPID id,
   BSTR*  pValue
);
```

#### <a name="parameters"></a>參數
 `id`

在要讀取之屬性的識別碼（`PROPID` 在 Wtypes.h 中定義為 `ULONG`）。

 `pValue`

脫銷傳回屬性值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則會傳回錯誤碼。 如果屬性不是 `BSTR` 類型，則傳回 `E_INVALIDARG`。

## <a name="remarks"></a>備註
 @No__t_0 是由 Windows 定義為以零為結尾的寬字元字串。

## <a name="see-also"></a>請參閱
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)