---
title: IDiaPropertyStorage：： ReadMultiple |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9cd1e419e1d08120274fc627a672eb52331ca50f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742877"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
從目前的屬性集讀取指定的屬性。

## <a name="syntax"></a>語法

```C++
HRESULT ReadMultiple( 
   ULONG          cpspec,
   PROPSPEC const rgpspec,
   PROPVARIANT    rgvar
);
```

#### <a name="parameters"></a>參數
 `cpspec`

在`rgpspec` 陣列中指定的屬性計數。 如果為零，則方法不會傳回任何屬性，但會以成功程式碼的形式傳回 `S_OK`。

 `rgpspec`

在要讀取的屬性陣列。 屬性可以透過屬性識別碼或選擇性的字串名稱來指定。 您不需要指定陣列中任何特定順序的屬性。 陣列可以包含重複的屬性，因此會在傳回簡單屬性時產生重複的屬性值。 非簡單屬性應該會在嘗試再次開啟時，傳回拒絕存取。 陣列可以包含屬性識別碼和字串識別碼的組合。 此陣列至少必須有 `cpspec` 的屬性值數目。

 `rgvar`

[in、out]要以每個屬性的值填入的 `PROPVARIANT` 結構陣列（在 VisualStudio 中）。 陣列的大小至少必須 `cpspec` 個元素。 呼叫端不需要初始化陣列中的值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 如果找不到一或多個屬性，則傳回 `S_FALSE`。 反之則會傳回錯誤碼。

## <a name="remarks"></a>備註
 如果找不到屬性，則 `rgvar` 陣列中的對應專案會包含類型為 `VT_EMPTY`的 `VARIANT`。

## <a name="see-also"></a>請參閱
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)