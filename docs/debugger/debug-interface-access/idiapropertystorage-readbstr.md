---
title: IDiaPropertyStorage：： ReadBSTR |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: c6e87c2ed168a262fc1a12f06fc6a18bcf73e7bc
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466592"
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
讀取 `BSTR` 屬性集中的值。

## <a name="syntax"></a>語法

```C++
HRESULT ReadBSTR ( 
   PROPID id,
   BSTR*  pValue
);
```

#### <a name="parameters"></a>參數
 `id`

在要讀取之屬性的識別碼（ `PROPID` 在 wtypes.h 中定義為 `ULONG` ）。

 `pValue`

脫銷傳回屬性值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。 `E_INVALIDARG`如果屬性不是型別，則傳回 `BSTR` 。

## <a name="remarks"></a>備註
 `BSTR`由 Windows 定義為以零為結尾的寬字元字串。

## <a name="see-also"></a>另請參閱
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)