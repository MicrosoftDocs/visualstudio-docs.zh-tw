---
title: IDiaPropertyStorage：： ReadULONGLONG |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadULONGLONG
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ab1459100d773e0f887c09f06d03cdfa8e578e35
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855540"
---
# <a name="idiapropertystoragereadulonglong"></a>IDiaPropertyStorage::ReadULONGLONG
讀取 `ULONGLONG` 屬性集中的值。

## <a name="syntax"></a>語法

```C++
HRESULT ReadULONGLONG ( 
   PROPID     id,
   ULONGLONG* pValue
);
```

#### <a name="parameters"></a>參數
 `id`

在要讀取之屬性的識別碼 (`PROPID` 在 wtypes.h 中定義為 `ULONG`) 。

 `pValue`

擴展傳回屬性值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回，否則會傳回 `S_OK` 錯誤碼。 `E_INVALIDARG`如果屬性不是型別，則會傳回 `ULONGLONG` 。

## <a name="remarks"></a>備註
 `ULONGLONG`由 Windows 定義為64位不帶正負號的整數。

## <a name="see-also"></a>另請參閱
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)