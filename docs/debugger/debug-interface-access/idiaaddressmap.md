---
description: 提供 DIA SDK 如何計算 debug 物件的虛擬和相對虛擬位址的控制權。
title: IDiaAddressMap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 085ba4e75eab1dd67585b3926b71edd5dce88d72
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159464"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
提供 DIA SDK 如何計算 debug 物件的虛擬和相對虛擬位址的控制權。

## <a name="syntax"></a>Syntax

```
IDiaAddressMap : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDiaAddressMap` 。

|方法|描述|
|------------|-----------------|
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|指出是否已為特定會話建立位址對應。|
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|指定是否應該使用位址對應來轉譯符號位址。|
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|指出是否已啟用相對虛擬位址的計算和使用。|
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|允許用戶端啟用或停用相對虛擬位址的計算。|
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|抓取目前的影像對齊。|
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|設定影像對齊。|
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|設定影像標頭，以啟用相對虛擬位址的轉譯。|
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|提供可支援影像版面配置翻譯的位址對應。|

## <a name="remarks"></a>備註
 此介面提供的控制項封裝在您提供的兩組資料中：影像標頭和位址對應。 大部分的用戶端會使用 [IDiaDataSource：： loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 方法來尋找影像的適當 debug 資訊，而且方法通常可以探索所有必要的標頭和地圖資料本身。 不過，有些用戶端會執行特殊處理和搜尋資料。 這類用戶端會使用介面的方法 `IDiaAddressMap` ，為 DIA SDK 提供搜尋結果。

## <a name="notes-for-callers"></a>呼叫者注意事項
 此介面可從 DIA 會話物件取得。 用戶端會 `QueryInterface` 在 DIA 會話物件介面（通常是 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)）上呼叫方法，以取得 `IDiaAddressMap` 介面。

## <a name="requirements"></a>規格需求
 標頭： Dia2。h

 程式庫： diaguids .lib

 DLL： msdia80.dll

## <a name="see-also"></a>另請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
