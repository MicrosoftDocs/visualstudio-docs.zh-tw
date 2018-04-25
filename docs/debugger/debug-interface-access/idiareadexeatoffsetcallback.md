---
title: IDiaReadExeAtOffsetCallback |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback interface
ms.assetid: 3c961641-3ce3-4bc3-bd6e-a802fa3bec49
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b60730a81ecc2948c51020fb7d7b4df766b93579
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="idiareadexeatoffsetcallback"></a>IDiaReadExeAtOffsetCallback
可讓用戶端應用程式提供的可執行檔所指定的檔案位置的位元組。  
  
## <a name="syntax"></a>語法  
  
```  
IDiaReadExeAtOffsetCallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDiaReadExeAtOffsetCallback`。  
  
|方法|描述|  
|------------|-----------------|  
|[IDiaReadExeAtOffsetCallback::ReadExecutableAt](../../debugger/debug-interface-access/idiareadexeatoffsetcallback-readexecutableat.md)|讀取指定的從可執行檔的指定位移處開始的位元組數目。|  
  
## <a name="remarks"></a>備註  
 用戶端應用程式會實作這個介面，以提供可執行檔到可執行檔的檔案使用絕對位移的位元組數。 若要使用的相對虛擬位址，實作[IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個方法為用戶端應用程式實作並傳遞給[idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)做為替代的方法，讀取檔案的方法。  
  
## <a name="requirements"></a>需求  
 標頭： Dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>另請參閱  
 [介面 （偵錯介面存取 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)