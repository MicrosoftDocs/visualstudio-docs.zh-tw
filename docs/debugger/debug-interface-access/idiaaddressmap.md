---
title: "IDiaAddressMap |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6cdd8c9d2e581df3e7b0ebeba092a212fb7a89f5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
可控制 DIA SDK 會以偵錯物件的虛擬和相對虛擬位址的計算。  
  
## <a name="syntax"></a>語法  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDiaAddressMap`。  
  
|方法|描述|  
|------------|-----------------|  
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|指出是否已為特定的工作階段建立對應的位址。|  
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|指定是否會用於將符號位址轉譯對應位址。|  
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|指出是否已啟用的計算方式與使用的相對虛擬位址。|  
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|允許用戶端啟用或停用的相對虛擬位址的計算。|  
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|擷取目前的影像對齊。|  
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|設定影像的對齊方式。|  
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|設定影像啟用的相對虛擬位址轉譯的標頭。|  
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|提供對應至支援映像配置翻譯的位址。|  
  
## <a name="remarks"></a>備註  
 此介面所提供的控制項封裝在兩組您提供的資料： 標頭的映像，位址對應。 大部分的用戶端使用[idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法來尋找適當的偵錯資訊的影像和方法可以通常探索的所有必要的標頭和對應資料本身。 但有些用戶端實作特殊的處理和搜尋資料。 這類用戶端使用的方法`IDiaAddressMap`介面，以提供 DIA SDK 的搜尋結果。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面是可從 DIA 工作階段物件。 用戶端呼叫`QueryInterface`DIA 工作階段物件介面上，通常方法[IDiaSession](../../debugger/debug-interface-access/idiasession.md)，擷取`IDiaAddressMap`介面。  
  
## <a name="requirements"></a>需求  
 標頭： Dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>請參閱  
 [介面 （偵錯介面存取 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)