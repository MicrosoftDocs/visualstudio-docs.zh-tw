---
title: IDiaPropertyStorage::Enum |Microsoft Docs
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
ms.openlocfilehash: e39693f63ea706ecdfa30a9ce0202444f51d4f57
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616101"
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
取得在這個集合中屬性的列舉值。

## <a name="syntax"></a>語法

```C++
HRESULT Enum ( 
   IEnumSTATPROPSTG** ppenum
);
```

#### <a name="parameters"></a>參數
 `ppenum`

[out]傳回`IEnumSTATPROPSTG`物件 （在 Microsoft.VisualStudio.OLE.Interop 命名空間中），表示屬性的列舉。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)