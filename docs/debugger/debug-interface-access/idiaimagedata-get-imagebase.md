---
title: IDiaImageData::get_imageBase | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7887fea30b04f4ebb6605169c58551122eccf73d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743442"
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

脫銷傳回建議的影像基底值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 由於映射基底衝突，映射可能會在載入時自動重定基底至未使用的記憶體位置。 這個方法會傳回在編譯時期儲存在模組中的基底提示（建議的記憶體位置）。

## <a name="see-also"></a>請參閱
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)