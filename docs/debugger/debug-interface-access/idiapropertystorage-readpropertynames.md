---
title: IDiaPropertyStorage：： ReadPropertyNames |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f554485ae56a9d5f190c749879545165d299531c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742862"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
針對指定的屬性識別碼，抓取對應的字串名稱。

## <a name="syntax"></a>語法

```C++
HRESULT ReadPropertyNames (
   ULONG         cpropid,
   PROPID const* rgpropid,
   BSTR*         rglpwstrName
);
```

#### <a name="parameters"></a>參數
 `cpropid`

在@No__t_0 中的屬性識別碼數目。

 `rgpropid`

在要取得名稱的屬性識別碼陣列（`PROPID` 在 Wtypes.h 中定義為 `ULONG`）。

 `rglpwstrName`

[in、out]指定之屬性識別碼的屬性名稱陣列。 陣列必須預先配置，才能保存要求的屬性名稱數目，而且至少必須要有 `cpropid``BSTR` 的字串。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 傳回的屬性名稱必須在不再需要時釋放（藉由呼叫 `SysFreeString` 函式）。

## <a name="see-also"></a>請參閱
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)