---
title: IDiaEnumStackFrames | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames interface
ms.assetid: 3d1e8403-c9fc-42ff-ae35-0ab9a5ed2ad7
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9453b9132543060819bbdabd0e504ec5dbae69e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62424020"
---
# <a name="idiaenumstackframes"></a>IDiaEnumStackFrames
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

列舉各種可用的堆疊框架。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IDiaEnumStackFrames::Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md)|從列舉序列中抓取指定數目的堆疊框架元素。|  
|[IDiaEnumStackFrames::Reset](../../debugger/debug-interface-access/idiaenumstackframes-reset.md)|將列舉順序重設為開頭。|  
  
## <a name="remarks"></a>備註  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 藉由呼叫 [IDiaStackWalker：： getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) 或 [IDiaStackWalker：： getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) 方法來取得這個介面。  
  
## <a name="example"></a>範例  
 這個範例會示範如何取得和使用 `IDiaEnumStackFrames` 介面。 如需函式的執行，請參閱 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) 介面 `PrintStackFrame` 。  
  
```cpp#  
void DumpStackFrames(IDiaStackWalker*     pStackWalker,  
                     IDiaStackWalkHelper* pStackWalkHelper,  
                     CV_CPU_TYPE_e        cpuType)  
{  
    if (pStackWalker != NULL && pStackWalkHelper != NULL)  
    {  
        CComPtr<IDiaEnumStackFrames> pEnumsFrames;  
        HRESULT hr;  
        hr = pStackWalker->getEnumFrames2(cpuType, pStackWalkHelper, &pEnumFrames);  
        if (SUCCEEDED(hr) && pEnumFrames != NULL)  
        {  
             CComPtr<IDiaStackFrame> pStackFrame;  
             DWORD celt = 0;  
  
             while (pEnumFrames->Next(1, &pStackFrame, &celt) == S_OK)  
             {  
                 PrintStackFrame(pStackFrame);  
             }  
             pStackFrame = NULL;  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>需求  
 標頭： Dia2。h  
  
 程式庫： diaguids .lib  
  
 DLL： msdia80.dll  
  
## <a name="see-also"></a>另請參閱  
 [ (Debug 介面存取 SDK) 介面 ](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
