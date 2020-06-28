---
title: IDiaPropertyStorage::ReadLONG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadLONG
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 697d93af1256d76e5448de5cbc34e04ffc26927f
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466578"
---
# <a name="idiapropertystoragereadlong"></a>IDiaPropertyStorage::ReadLONG
讀取 `LONG` 屬性集中的值。

## <a name="syntax"></a>語法

```C++
HRESULT ReadDLONG ( 
   PROPID id,
   LONG*  pValue
);
```

#### <a name="parameters"></a>參數
 `id`

在要讀取之屬性的識別碼（ `PROPID` 在 wtypes.h 中定義為 `ULONG` ）。

 `pValue`

脫銷傳回屬性值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。 `E_INVALIDARG`如果屬性不是型別，則傳回 `LONG` 。

## <a name="remarks"></a>備註
 `LONG`由 Windows 定義為32位帶正負號的整數。

## <a name="see-also"></a>另請參閱
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)