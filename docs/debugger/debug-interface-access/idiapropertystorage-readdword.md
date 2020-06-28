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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d654fdfdfeacc9071081a65f3ad94b2ad240ae5
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466585"
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

在要讀取之屬性的識別碼（ `PROPID` 在 wtypes.h 中定義為 `ULONG` ）。

 `pValue`

脫銷傳回屬性值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。 `E_INVALIDARG`如果屬性不是型別，則傳回 `DWORD` 。

## <a name="remarks"></a>備註
 `DWORD`由 Windows 定義為32位不帶正負號的整數。

## <a name="see-also"></a>另請參閱
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)