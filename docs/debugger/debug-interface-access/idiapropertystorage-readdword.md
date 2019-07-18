---
title: IDiaPropertyStorage::ReadDWORD |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 5b4709a218f6586320e96f79ea8a9f423f537c7f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839650"
---
# <a name="idiapropertystoragereaddword"></a>IDiaPropertyStorage::ReadDWORD
讀取`DWORD`屬性集合中的值。

## <a name="syntax"></a>語法

```C++
HRESULT ReadDWORD ( 
   PROPID id,
   DWORD* pValue
);
```

#### <a name="parameters"></a>參數
 `id`

[in]要讀取之屬性的識別項 (`PROPID`定義為 WTypes.h 中`ULONG`)。

 `pValue`

[out]傳回屬性值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則會傳回錯誤碼。 傳回`E_INVALIDARG`如果屬性不是型別的`DWORD`。

## <a name="remarks"></a>備註
 A`DWORD`由 Windows 與 32 位元不帶正負號的整數所定義。

## <a name="see-also"></a>另請參閱
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)