---
title: IDiaEnumSourceFiles | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles interface
ms.assetid: 5c0779a6-a2ea-408a-90da-ebdecf2b83c0
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8b095515be5e3c032667c96d8b13d92aa5995c7f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943258"
---
# <a name="idiaenumsourcefiles"></a>IDiaEnumSourceFiles
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

列舉各種資料來源中包含的原始程式檔。  
  
## <a name="syntax"></a>語法  
  
```  
IDiaEnumSourceFiles : IUknown  
```  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDiaEnumSourceFiles`。  
  
|方法|描述|  
|------------|-----------------|  
|[IDiaEnumSourceFiles::get__NewEnum](../../debugger/debug-interface-access/idiaenumsourcefiles-get-newenum.md)|擷取`IEnumVARIANT Interface`這個列舉值的版本。|  
|[IDiaEnumSourceFiles::get_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md)|擷取來源檔案的數目。|  
|[IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)|透過索引中擷取原始程式檔。|  
|[IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)|擷取列舉序列中的原始程式檔中指定的數目。|  
|[IDiaEnumSourceFiles::Skip](../../debugger/debug-interface-access/idiaenumsourcefiles-skip.md)|略過列舉序列中的原始程式檔指定的數目。|  
|[IDiaEnumSourceFiles::Reset](../../debugger/debug-interface-access/idiaenumsourcefiles-reset.md)|將列舉型別序列重設到開頭。|  
|[IDiaEnumSourceFiles::Clone](../../debugger/debug-interface-access/idiaenumsourcefiles-clone.md)|建立列舉值，包含目前的列舉值相同的列舉型別狀態。|  
  
## <a name="remarks"></a>備註  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 取得這個介面，藉由呼叫`QueryInterface`方法[IDiaTable](../../debugger/debug-interface-access/idiatable.md)物件。 請參閱詳細資料的範例。  
  
## <a name="example"></a>範例  
 此範例示範如何取得`IDiaEnumSourceFiles`DIA 工作階段物件中的資料表清單中的介面。 如需存取原始程式檔資訊的範例，請參閱 < [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)介面。  
  
```cpp#  
  
IDiaEnumSourceFiles* GetEnumSourceFiless(IDiaSession *pSession)  
{  
    IDiaEnumSourceFiles * pUnknown    = NULL;  
    REFIID                iid         = __uuidof(IDiaEnumSourceFiles);  
    IDiaEnumTables*       pEnumTables = NULL;  
    IDiaTable*            pTable      = NULL;  
    ULONG                 celt        = 0;  
  
    if (pSession->getEnumTables(&pEnumTables) != S_OK)  
    {  
        wprintf(L"ERROR - GetTable() getEnumTables\n");  
        return NULL;  
    }  
    while (pEnumTables->Next(1, &pTable, &celt) == S_OK && celt == 1)  
    {  
        // There is only one table that matches the given iid  
        HRESULT hr = pTable->QueryInterface(iid, (void**)&pUnknown);  
        pTable->Release();  
        if (hr == S_OK)  
        {  
            break;  
        }  
    }  
    pEnumTables->Release();  
    return pUnknown;  
}  
```  
  
## <a name="requirements"></a>需求  
 標頭：dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>另請參閱  
 [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
