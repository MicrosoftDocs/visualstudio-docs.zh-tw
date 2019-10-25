---
title: IDiaAddressMap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e06acf045ce1893762d5c898752dd6bc40de50a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744984"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
可讓您控制 DIA SDK 如何計算 debug 物件的虛擬和相對虛擬位址。

## <a name="syntax"></a>語法

```
IDiaAddressMap : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示 `IDiaAddressMap` 的方法。

|方法|描述|
|------------|-----------------|
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|指出是否已建立特定會話的位址對應。|
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|指定是否應使用位址對應來轉譯符號位址。|
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|指出是否已啟用相對虛擬位址的計算和使用。|
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|允許用戶端啟用或停用相對虛擬位址的計算。|
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|抓取目前的影像對齊。|
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|設定影像對齊。|
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|設定影像標頭，以啟用相對虛擬位址的轉譯。|
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|提供位址對應以支援影像版面配置翻譯。|

## <a name="remarks"></a>備註
 這個介面所提供的控制項會封裝在您提供的兩組資料中：影像標頭和位址對應。 大部分的用戶端會使用[IDiaDataSource：： loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法來尋找影像的適當偵錯工具資訊，而方法通常會探索所有必要的標頭並對應資料本身。 不過，有些用戶端會執行特殊處理和搜尋資料。 這類用戶端會使用 `IDiaAddressMap` 介面的方法，為 DIA SDK 提供搜尋結果。

## <a name="notes-for-callers"></a>呼叫者的注意事項
 此介面可從 DIA 會話物件取得。 用戶端會在 DIA 會話物件介面（通常是[IDiaSession](../../debugger/debug-interface-access/idiasession.md)）上呼叫 `QueryInterface` 方法，以取出 `IDiaAddressMap` 介面。

## <a name="requirements"></a>需求
 標頭： Dia2。h

 程式庫： diaguids

 DLL： msdia80

## <a name="see-also"></a>請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)