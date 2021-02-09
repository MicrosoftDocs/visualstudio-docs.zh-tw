---
title: IDiaPropertyStorage::ReadBOOL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 60d985851b1d547eed4306762c453bdd480bb1a9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855589"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
讀取 `BOOL` 屬性集中的值。

## <a name="syntax"></a>語法

```C++
HRESULT ReadBOOL ( 
   PROPID id,
   BOOL*  pValue
);
```

#### <a name="parameters"></a>參數
 `id`

在要讀取之屬性的識別碼 (`PROPID` 在 wtypes.h 中定義為 `ULONG`) 。

 `pValue`

擴展傳回屬性值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回，否則會傳回 `S_OK` 錯誤碼。 `E_INVALIDARG`如果屬性不是型別，則會傳回 `BOOL` 。

## <a name="remarks"></a>備註
 針對一致的結果，請解讀 `BOOL` 值，讓非零值為 `TRUE` ，而零為 `FALSE` 。

## <a name="see-also"></a>另請參閱
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)