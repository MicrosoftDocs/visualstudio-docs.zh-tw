---
description: 設定影像對齊。
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0c3027332018441efd132cc941d16aab3bcab594
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158365"
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
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
  (載入的可執行檔) 的影像會對齊指定的記憶體界限。 這種對齊方式可能會受到目前系統架構和編譯和連結時間選項的影響。 影像對齊一律為位元組界限。 下列影像對齊值有效：1、2、4、8、16、32和64位元組界限。

 您可以呼叫 [IDiaAddressMap：： get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) 方法來抓取目前的影像對齊。

> [!NOTE]
> 此映射已在可呼叫這個方法時載入。 `put_imageAlign`方法通常是在影像已移動或變更，且需要新的對齊時使用。

## <a name="see-also"></a>另請參閱
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)
