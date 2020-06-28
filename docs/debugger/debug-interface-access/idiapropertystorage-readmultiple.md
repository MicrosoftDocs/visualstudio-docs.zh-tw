---
title: IDiaPropertyStorage：： ReadMultiple |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 8681032840f09bcc4a90df66b3a6f37d664739ab
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466571"
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

在陣列中指定的屬性計數 `rgpspec` 。 如果為零，則方法不會傳回任何屬性，但會傳回 `S_OK` 為成功程式碼。

 `rgpspec`

在要讀取的屬性陣列。 屬性可以透過屬性識別碼或選擇性的字串名稱來指定。 您不需要指定陣列中任何特定順序的屬性。 陣列可以包含重複的屬性，因此會在傳回簡單屬性時產生重複的屬性值。 非簡單屬性應該會在嘗試再次開啟時，傳回拒絕存取。 陣列可以包含屬性識別碼和字串識別碼的組合。 此陣列至少必須有 `cpspec` 屬性值的數目。

 `rgvar`

[in、out]`PROPVARIANT`要以每個屬性的值填入的結構陣列（在 VisualStudio 中）。 陣列的大小至少必須為個 `cpspec` 元素。 呼叫端不需要初始化陣列中的值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果找不到一或多個屬性，則傳回。 反之則會傳回錯誤碼。

## <a name="remarks"></a>備註
 如果找不到屬性，則陣列中對應的專案會 `rgvar` 包含 `VARIANT` 具有類型的 `VT_EMPTY` 。

## <a name="see-also"></a>另請參閱
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)