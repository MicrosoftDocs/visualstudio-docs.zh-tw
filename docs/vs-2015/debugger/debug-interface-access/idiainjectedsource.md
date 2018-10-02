---
title: IDiaInjectedSource |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource interface
ms.assetid: 75192c5c-812d-4675-9dc5-4c2cff3ba503
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 643c0208624fbf5ac121901478b77ff49cdf637d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490513"
---
# <a name="idiainjectedsource"></a>IDiaInjectedSource
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDiaInjectedSource](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiainjectedsource)。  
  
存取插入儲存在 DIA 資料來源中的原始程式碼。  
  
## <a name="syntax"></a>語法  
  
```  
IDiaInjectedSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDiaInjectedSource`。  
  
|方法|描述|  
|------------|-----------------|  
|[IDiaInjectedSource::get_crc](../../debugger/debug-interface-access/idiainjectedsource-get-crc.md)|擷取從來源程式碼位元組計算的循環冗餘檢查 (CRC)。|  
|[IDiaInjectedSource::get_length](../../debugger/debug-interface-access/idiainjectedsource-get-length.md)|擷取的程式碼的位元組數目。|  
|[IDiaInjectedSource::get_filename](../../debugger/debug-interface-access/idiainjectedsource-get-filename.md)|擷取來源檔案名稱。|  
|[IDiaInjectedSource::get_objectFilename](../../debugger/debug-interface-access/idiainjectedsource-get-objectfilename.md)|擷取來源已編譯的物件檔案名稱。|  
|[IDiaInjectedSource::get_virtualFilename](../../debugger/debug-interface-access/idiainjectedsource-get-virtualfilename.md)|擷取指定給非檔案來源的程式碼; 的名稱也就是插入的程式碼。|  
|[IDiaInjectedSource::get_sourceCompression](../../debugger/debug-interface-access/idiainjectedsource-get-sourcecompression.md)|擷取來源所用的壓縮的指標。|  
|[IDiaInjectedSource::get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)|擷取來源的程式碼位元組。|  
  
## <a name="remarks"></a>備註  
 插入的來源是在編譯期間插入的文字。 這不表示前置處理器`#include`c + + 中使用。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 取得這個介面，藉由呼叫[idiaenuminjectedsources:: Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)或是[idiaenuminjectedsources:: Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)方法。 請參閱[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)介面，如需範例，取得`IDiaInjectedSource`介面。  
  
## <a name="example"></a>範例  
 此範例會顯示可從資料`IDiaInjectedSource`介面。 使用替代方法[IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)介面，請參閱中的範例[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)介面。  
  
```cpp#  
void PrintInjectedSource(IDiaInjectedSource* pSource)  
{  
    ULONGLONG codeLength      = 0;  
    DWORD     crc             = 0;  
    DWORD     compressionType = 0;  
    BSTR      sourceFilename  = NULL;  
    BSTR      objectFilename  = NULL;  
    BSTR      virtualFilename = NULL;  
  
    std::cout << "Injected Source:" << std::endl;  
    if (pSource != NULL)  
    {  
        if (pSource->get_crc(&crc) == S_OK &&  
            pSource->get_sourceCompression(&compressionType) == S_OK &&  
            pSource->get_length(&codeLength) == S_OK)  
        {  
            wprintf(L"  crc = %lu\n", crc);  
            wprintf(L"  code length = %I64u\n",codeLength);  
            wprintf(L"  compression type code = %lu\n", compressionType);  
        }  
  
        wprintf(L"  source filename: ");  
        if (pSource->get_filename(&sourceFilename) == S_OK)  
        {  
            wprintf(L"%s", sourceFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        wprintf(L"  object filename: ");  
        if (pSource->get_filename(&objectFilename) == S_OK)  
        {  
            wprintf(L"%s", objectFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        wprintf(L"  virtual filename: ");  
        if (pSource->get_filename(&virtualFilename) == S_OK)  
        {  
            wprintf(L"%s", virtualFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        SysFreeString(sourceFilename);  
        SysFreeString(objectFilename);  
        SysFreeString(virtualFilename);  
    }  
}  
```  
  
## <a name="requirements"></a>需求  
 標頭： Dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>另請參閱  
 [介面 （偵錯介面存取 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiaenuminjectedsources:: Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)   
 [Idiaenuminjectedsources:: Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)



