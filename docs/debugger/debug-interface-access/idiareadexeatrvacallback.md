---
title: IDiaReadExeAtRVACallback |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e00ce2e1286c2309a11984f9bde23aa74071a076
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53859288"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
可讓用戶端應用程式提供的可執行檔的相對虛擬位址所指定的位元組。  
  
## <a name="syntax"></a>語法  
  
```  
IDiaReadExeAtRVACallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDiaReadExeAtRVACallback`。  
  
|方法|說明|  
|------------|-----------------|  
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|讀取指定起始於指定相對虛擬位址 (RVA) 從可執行檔的位元組數目。|  
  
## <a name="remarks"></a>備註  
 用戶端應用程式會實作這個介面，以便使用可執行檔的檔案的相對虛擬位址之可執行檔的位元組。 若要使用的絕對檔案位移，實作[IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個方法是藉由將用戶端應用程式，並傳遞給[idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法作為替代方法來讀取檔案。  
  
## <a name="requirements"></a>需求  
 標頭：dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>請參閱  
 [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)