---
title: IDiaPropertyStorage：： ReadDWORD |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadDWORD
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b85c8095ca4d730dd74054c976d9a5bf217f1cc1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855575"
---
# <a name="idiapropertystoragereaddword"></a>IDiaPropertyStorage::ReadDWORD
讀取 `DWORD` 屬性集中的值。

## <a name="syntax"></a>語法

```C++
HRESULT ReadDWORD ( 
   PROPID id,
   DWORD* pValue
);
```

#### <a name="parameters"></a>參數
 `id`

在要讀取之屬性的識別碼 (`PROPID` 在 wtypes.h 中定義為 `ULONG`) 。

 `pValue`

擴展傳回屬性值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回，否則會傳回 `S_OK` 錯誤碼。 `E_INVALIDARG`如果屬性不是型別，則會傳回 `DWORD` 。

## <a name="remarks"></a>備註
 `DWORD`由 Windows 定義為32位不帶正負號的整數。

## <a name="see-also"></a>另請參閱
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)