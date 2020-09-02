---
title: IDiaLoadCallback2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2 interface
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5c1225d75ea857fe34906daeb4792524fde4bc6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538807"
---
# <a name="idialoadcallback2"></a>IDiaLoadCallback2
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

從 DIA 符號尋找程式接收回呼，以允許在尋找進程上加諸限制。  
  
## <a name="syntax"></a>語法  
  
```  
IDiaLoadCallback2 : IDiaLoadCallback  
```  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) 介面中的方法，此介面會公開下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|判斷是否在原始的 debug 目錄中尋找 .pdb 檔。|  
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|判斷是否允許在 .exe 檔案所在的路徑中尋找 .pdb 檔。|  
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|判斷是否允許從 dbg 檔案尋找 debug 資訊。|  
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|決定是否允許在系統根目錄中搜尋 .pdb 檔。|  
  
## <a name="remarks"></a>備註  
 用戶端應用程式會執行這個介面，並在 [IDiaDataSource：： loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 方法的呼叫中提供它的參考。 也請記得在 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) 介面中執行所有方法。  
  
## <a name="requirements"></a>需求  
 標頭： Dia2。h  
  
 程式庫： diaguids .lib  
  
 DLL： msdia80.dll  
  
## <a name="see-also"></a>另請參閱  
 [ (Debug 介面存取 SDK) 介面 ](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource：： loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)
