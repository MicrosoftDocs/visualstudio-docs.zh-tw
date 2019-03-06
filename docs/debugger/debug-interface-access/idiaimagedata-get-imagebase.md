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
ms.openlocfilehash: de8c333391530cd86c6fc66a8e6c36ce8cfecd5f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56623862"
---
# <a name="idiaimagedatagetimagebase"></a>IDiaImageData::get_imageBase
擷取以為基礎的映像的記憶體位置。

## <a name="syntax"></a>語法

```C++
HRESULT get_imageBase ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]傳回建議的映像的基底值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 映像基底的衝突，因為映像可能重定基底自動未使用的記憶體位置載入時。 這個方法會傳回已儲存在模組中，在編譯時期的基底提示 （建議的記憶體位置）。

## <a name="see-also"></a>請參閱
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)