---
title: IDiaPropertyStorage：： Enum |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::Enum
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00bd1ea5e20d30fa1d2c32101b56f55d169f1ce2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742948"
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
取得此集合中屬性的列舉值。

## <a name="syntax"></a>語法

```C++
HRESULT Enum ( 
   IEnumSTATPROPSTG** ppenum
);
```

#### <a name="parameters"></a>參數
 `ppenum`

脫銷傳回 `IEnumSTATPROPSTG` 物件（在 VisualStudio 中），代表屬性的列舉。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)