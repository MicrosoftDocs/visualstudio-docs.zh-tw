---
title: IDiaStackWalker | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d6f5f5c3fa70c022175208cee492f3c0e752826e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144675"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

提供方法，以使用 .pdb 檔案中的資訊來進行堆疊逐步解說。  
  
## <a name="syntax"></a>語法  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法 `IDiaStackWalker` 。  
  
|方法|描述|  
|------------|-----------------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|捕獲 x86 平臺的堆疊框架列舉值。|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|抓取特定平臺類型的堆疊框架列舉值。|  
  
## <a name="remarks"></a>備註  
 這個介面是用來取得已載入模組的堆疊框架清單。 每個方法都會傳遞 (用戶端應用程式所執行的 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) 物件，) 提供建立堆疊框架清單所需的資訊。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 藉由呼叫 `CoCreateInstance` 具有類別識別碼和之介面識別碼的方法，即可取得這個介面 `CLSID_DiaStackWalker` `IID_IDiaStackWalker` 。 此範例顯示如何取得此介面。  
  
## <a name="example"></a>範例  
 此範例顯示如何取得 `IDiaStackWalker` 介面。  
  
```cpp#  
  
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
 標頭： Dia2。h  
  
 程式庫： diaguids .lib  
  
 DLL： msdia80.dll  
  
## <a name="see-also"></a>另請參閱  
 [ (Debug 介面存取 SDK) 介面 ](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
