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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839676"
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

## <a name="see-also"></a>另請參閱
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)