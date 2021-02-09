---
title: IDiaPropertyStorage：： Enum |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::Enum
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8972fa93ebae30fc64839324106d068e27577434
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864646"
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
取得此集合內屬性的列舉值。

## <a name="syntax"></a>語法

```C++
HRESULT Enum ( 
   IEnumSTATPROPSTG** ppenum
);
```

#### <a name="parameters"></a>參數
 `ppenum`

擴展傳回 `IEnumSTATPROPSTG` VisualStudio 命名空間中 (的物件，) 代表屬性的列舉。

## <a name="return-value"></a>傳回值
 如果成功，則傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)