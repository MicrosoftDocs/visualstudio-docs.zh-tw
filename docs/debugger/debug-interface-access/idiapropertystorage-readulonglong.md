---
title: IDiaPropertyStorage::ReadULONGLONG |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadULONGLONG
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f365578aba73ed94bdcd1d87801fc53030cfecdb
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616010"
---
# <a name="idiapropertystoragereadulonglong"></a>IDiaPropertyStorage::ReadULONGLONG
讀取`ULONGLONG`屬性集合中的值。

## <a name="syntax"></a>語法

```C++
HRESULT ReadULONGLONG ( 
   PROPID     id,
   ULONGLONG* pValue
);
```

#### <a name="parameters"></a>參數
 `id`

[in]要讀取之屬性的識別項 (`PROPID`定義為 WTypes.h 中`ULONG`)。

 `pValue`

[out]傳回屬性值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則會傳回錯誤碼。 傳回`E_INVALIDARG`如果屬性不是型別的`ULONGLONG`。

## <a name="remarks"></a>備註
 A`ULONGLONG`為 64 位元不帶正負號整數的 Windows 所定義。

## <a name="see-also"></a>請參閱
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)