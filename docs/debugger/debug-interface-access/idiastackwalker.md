---
title: "IDiaStackWalker |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e651c8ba8bee152121b96b14613144768a56cc2f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiastackwalker"></a>IDiaStackWalker
提供方法，以執行堆疊查核行程使用.pdb 檔案中的資訊。  
  
## <a name="syntax"></a>語法  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDiaStackWalker`。  
  
|方法|說明|  
|------------|-----------------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|擷取堆疊框架的列舉值適用於 x86 平台。|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|擷取特定平台類型的堆疊框架的列舉值。|  
  
## <a name="remarks"></a>備註  
 這個介面用來取得載入模組的堆疊框架的清單。 每個方法傳遞[IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) （用戶端應用程式所實作） 會提供所需的資訊建立堆疊框架的清單物件。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面透過呼叫`CoCreateInstance`方法與類別識別項`CLSID_DiaStackWalker`而介面 ID 的`IID_IDiaStackWalker`。 此範例示範如何取得此介面。  
  
## <a name="example"></a>範例  
 這個範例示範如何取得`IDiaStackWalker`介面。  
  
```C++  
  
      IDiaStackWalker* pStackWalker;  
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaStackWalker,  
                              (void**) &pStackWalker);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## <a name="requirements"></a>需求  
 標頭： Dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>另請參閱  
 [介面 （偵錯介面存取 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)