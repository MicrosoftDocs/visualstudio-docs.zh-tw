---
description: 抓取影像應依據的記憶體位置。
title: IDiaImageData::get_imageBase | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 82f80f95689a176118d5be6dcc5cfe4fdb903e0f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148448"
---
# <a name="idiaimagedataget_imagebase"></a>IDiaImageData::get_imageBase
抓取影像應依據的記憶體位置。

## <a name="syntax"></a>語法

```C++
HRESULT get_imageBase ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回建議的影像基底值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 由於映射基底衝突，映射可能會在載入時自動重定基底至未使用的記憶體位置。 這個方法會傳回基底提示， (在編譯時期儲存在模組中的建議記憶體位置) 。

## <a name="see-also"></a>另請參閱
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)
