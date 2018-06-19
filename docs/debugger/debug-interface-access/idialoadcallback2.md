---
title: IDiaLoadCallback2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2 interface
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09e835d8a7bfe0bc5d7ae06f0bac457126d21956
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31466779"
---
# <a name="idialoadcallback2"></a>IDiaLoadCallback2
從允許的限制，以可加諸於尋找處理程序，找出程序 DIA 符號接收回呼。  
  
## <a name="syntax"></a>語法  
  
```  
IDiaLoadCallback2 : IDiaLoadCallback  
```  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了在[IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)介面，這個介面會公開下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|判斷是否搜尋原始的偵錯目錄中的.pdb 檔案。|  
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|決定如果尋找.pdb 檔案中的.exe 檔案所在位置的路徑。|  
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|決定尋找偵錯資訊是否允許從.dbg 檔案。|  
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|決定系統根目錄中是否允許搜尋.pdb 檔案。|  
  
## <a name="remarks"></a>備註  
 用戶端應用程式會實作這個介面，並提供給它的呼叫中的參考[idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法。 請記得要實作的方法中的所有[IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)以及介面。  
  
## <a name="requirements"></a>需求  
 標頭： Dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>另請參閱  
 [介面 （偵錯介面存取 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)