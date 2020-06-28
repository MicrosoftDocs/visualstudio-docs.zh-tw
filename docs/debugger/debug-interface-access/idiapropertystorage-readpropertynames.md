---
title: IDiaPropertyStorage：： ReadPropertyNames |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 257546e54cb04713f2f13892ec782aca1712cfba
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466515"
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

在要取得名稱的屬性識別碼陣列（ `PROPID` 在 wtypes.h 中定義為 `ULONG` ）。

 `rglpwstrName`

[in、out]指定之屬性識別碼的屬性名稱陣列。 必須預先配置陣列，以保存要求的屬性名稱數目，而且必須能夠保存至少個 `cpropid``BSTR` 字串。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="remarks"></a>備註
 傳回的屬性名稱必須在不再需要時釋放（藉由呼叫函式 `SysFreeString` ）。

## <a name="see-also"></a>另請參閱
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)