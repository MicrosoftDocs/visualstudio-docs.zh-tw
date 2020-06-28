---
title: IDiaAddressMap::get_imageAlign | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_imageAlign method
ms.assetid: f1ba8071-669c-4cf7-9ac0-02f26d99f366
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 814381cb4792d9c21825ab1be5ebc4da415bc974
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468585"
---
# <a name="idiaaddressmapget_imagealign"></a>IDiaAddressMap::get_imageAlign
抓取目前的影像對齊。

## <a name="syntax"></a>語法

```C++
HRESULT get_imageAlign ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回可執行檔的影像對齊值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="remarks"></a>備註
 影像會根據載入和建立映射的方式，對齊特定的記憶體界限。 對齊通常是在1、2、4、8、16、32或64位元組界限上。 影像對齊可以透過呼叫[IDiaAddressMap：:p ut_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)方法來設定。

## <a name="see-also"></a>另請參閱
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)