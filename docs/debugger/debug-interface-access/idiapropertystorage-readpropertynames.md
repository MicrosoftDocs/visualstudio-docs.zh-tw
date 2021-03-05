---
description: 針對指定的屬性識別碼，抓取對應的字串名稱。
title: IDiaPropertyStorage：： ReadPropertyNames |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cbb6d511a6be9ed408b076162a3d00d22705075a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148140"
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

在中的屬性識別碼數目 `rgpropid` 。

 `rgpropid`

在要取得名稱的屬性識別碼陣列 (`PROPID` 是在 wtypes.h 中定義為 `ULONG`) 。

 `rglpwstrName`

[in，out]指定之屬性識別碼的屬性名稱陣列。 陣列必須預先配置以保存所要求的屬性名稱數目，而且必須至少能保留 `cpropid``BSTR` 字串。

## <a name="return-value"></a>傳回值
 如果成功，則傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="remarks"></a>備註
 傳回的屬性名稱必須在不再需要時，呼叫函式) 來釋出 (`SysFreeString` 。

## <a name="see-also"></a>另請參閱
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
