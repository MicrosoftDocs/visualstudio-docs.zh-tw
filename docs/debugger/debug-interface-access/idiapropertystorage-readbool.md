---
title: IDiaPropertyStorage::ReadBOOL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d776e37bab189e61d0264f4cbda24f89cb4501ce
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742930"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
讀取屬性集內的 `BOOL` 值。

## <a name="syntax"></a>語法

```C++
HRESULT ReadBOOL ( 
   PROPID id,
   BOOL*  pValue
);
```

#### <a name="parameters"></a>參數
 `id`

在要讀取之屬性的識別碼（`PROPID` 在 Wtypes.h 中定義為 `ULONG`）。

 `pValue`

脫銷傳回屬性值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則會傳回錯誤碼。 如果屬性不是 `BOOL` 類型，則傳回 `E_INVALIDARG`。

## <a name="remarks"></a>備註
 若要取得一致的結果，請解讀 `BOOL` 值，讓非零值 `TRUE`，並 `FALSE` 零。

## <a name="see-also"></a>請參閱
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)