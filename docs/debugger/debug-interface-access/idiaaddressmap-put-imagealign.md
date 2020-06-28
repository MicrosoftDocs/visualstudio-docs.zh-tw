---
title: IDiaAddressMap::put_imageAlign | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ad9a97dd2e50b5bc131975321306bf8d9d52501e
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468564"
---
# <a name="idiaaddressmapput_imagealign"></a>IDiaAddressMap::put_imageAlign
設定影像對齊。

## <a name="syntax"></a>語法

```C++
HRESULT put_imageAlign ( 
   DWORD NewVal
);
```

#### <a name="parameters"></a>參數
 NewVal

在可執行檔的新影像對齊值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="remarks"></a>備註
 影像（已載入的可執行檔）會對齊指定的記憶體界限。 這項對齊可能會受到目前系統架構和編譯和連結時間選項的影響。 影像對齊一律會在位元組界限上。 下列影像對齊值有效：1、2、4、8、16、32和64位元組界限。

 您可以呼叫[IDiaAddressMap：： get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)方法來抓取目前的影像對齊。

> [!NOTE]
> 此映射已由呼叫此方法時載入。 `put_imageAlign`當影像已移動或變更，而且需要新的對齊時，通常會使用此方法。

## <a name="see-also"></a>另請參閱
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)