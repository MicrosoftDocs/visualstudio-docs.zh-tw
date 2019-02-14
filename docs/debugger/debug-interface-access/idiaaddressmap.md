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
ms.openlocfilehash: 0880009e6ae46f0d5ae89eb4332ddba57fa26394
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031262"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
可讓您控制 DIA SDK 如何計算偵錯物件的虛擬和相對虛擬位址。  
  
## <a name="syntax"></a>語法  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDiaAddressMap`。  
  
|方法|描述|  
|------------|-----------------|  
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|指出是否已為特定的工作階段建立對應的位址。|  
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|指定對應位址是否應該用來將符號位址轉譯。|  
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|指出是否已啟用的計算方式與使用相對虛擬位址。|  
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|允許啟用或停用的相對虛擬位址計算用戶端。|  
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|擷取目前的影像對齊方式。|  
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|設定的影像對齊方式。|  
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|設定映像標頭，以啟用的相對虛擬位址轉譯。|  
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|提供支援映像的版面配置轉譯對應的位址。|  
  
## <a name="remarks"></a>備註  
 此介面所提供的控制會封裝在兩個您所提供的資料集： 映像標頭，並解決對應。 大部分的用戶端會使用[idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法來尋找適當的偵錯資訊，如影像和方法可以通常探索的所有必要的標頭和對應資料本身。 不過有些用戶端實作特殊的處理和搜尋資料。 此類用戶端使用的方法`IDiaAddressMap`介面，以提供 DIA SDK，使用搜尋結果。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面是可從 DIA 工作階段物件。 用戶端會呼叫`QueryInterface`DIA 工作階段物件介面上，通常方法[IDiaSession](../../debugger/debug-interface-access/idiasession.md)，以擷取`IDiaAddressMap`介面。  
  
## <a name="requirements"></a>需求  
 標頭：dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>請參閱  
 [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)