---
title: IDiaEnumSegments::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Clone method
ms.assetid: 93deaac6-72ab-4408-ba14-66174a618757
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 59cfde0b935ec43f6b439d2d2cf58b39d2ac9aa7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856408"
---
# <a name="idiaenumsegmentsclone"></a>IDiaEnumSegments::Clone
建立包含與目前列舉值相同列舉狀態的列舉值。

## <a name="syntax"></a>語法

```C++
HRESULT Clone ( 
   IDiaEnumSegments** ppenum
);
```

#### <a name="parameters"></a>參數
 ppenum

擴展傳回包含重複列舉值的 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md) 物件。 區段不會重複，只會複製列舉值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)