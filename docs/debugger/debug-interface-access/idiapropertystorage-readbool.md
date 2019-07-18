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
ms.openlocfilehash: c5cc189283d6e9910b0b01d3d3e1ca28165bf500
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839689"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
讀取`BOOL`屬性集合中的值。

## <a name="syntax"></a>語法

```C++
HRESULT ReadBOOL ( 
   PROPID id,
   BOOL*  pValue
);
```

#### <a name="parameters"></a>參數
 `id`

[in]要讀取之屬性的識別項 (`PROPID`定義為 WTypes.h 中`ULONG`)。

 `pValue`

[out]傳回屬性值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則會傳回錯誤碼。 傳回`E_INVALIDARG`如果屬性不是型別的`BOOL`。

## <a name="remarks"></a>備註
 取得一致的結果，解譯`BOOL`值，以讓非零的值為`TRUE`為零，而且`FALSE`。

## <a name="see-also"></a>另請參閱
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)