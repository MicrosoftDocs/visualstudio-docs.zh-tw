---
title: IDiaEnumSymbolsByAddr | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsbyAddr interface
ms.assetid: 37d3dcdf-e4fa-4354-b5e1-8843566b52ac
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5a4b36b27c43beaa0f975adc5ddfa0a4feb9c069
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940254"
---
# <a name="idiaenumsymbolsbyaddr"></a>IDiaEnumSymbolsByAddr
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

列舉各種資料來源中包含的符號位址。  
  
## <a name="syntax"></a>語法  
  
```  
IDiaEnumSymbolsByAddr : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDiaEnumSymbolsByAddr`。  
  
|方法|描述|  
|------------|-----------------|  
|[IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)|將列舉值中執行查閱的區段和位移。|  
|[IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)|將列舉值，依相對虛擬位址 (RVA) 中執行查閱。|  
|[IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)|將列舉值的虛擬位址 (VA) 中執行查閱。|  
|[IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)|擷取位址中順序的下一個符號。 更新列舉值位置所擷取的項目數目。|  
|[IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)|擷取位址中順序的上一個符號。 更新列舉值位置所擷取的項目數目。|  
|[IDiaEnumSymbolsByAddr::Clone](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-clone.md)|建立物件的複本。|  
  
## <a name="remarks"></a>備註  
 這個介面會提供依位址的符號。 若要使用符號，例如依類型分組`SymTagUDT`（使用者定義型別） 或`SymTagBaseClass`，使用[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 取得這個介面，藉由呼叫[idiasession:: Getsymbolsbyaddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)方法。  
  
## <a name="example"></a>範例  
 此函式會顯示的名稱和位址依相對虛擬位址的所有符號。  
  
```cpp#  
void ShowSymbolsByAddress(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSymbolsByAddr> pEnumByAddr;  
    if ( FAILED( psession->getSymbolsByAddr( &pEnumByAddr ) ) )  
    {  
        Fatal( "getSymbolsByAddr" );  
    }  
    CComPtr<IDiaSymbol> pSym;  
    if ( FAILED( pEnumByAddr->symbolByAddr( 1, 0, &pSym ) ) )  
    {  
        Fatal( "symbolByAddr" );  
    }  
    DWORD rvaLast = 0;  
    if ( pSym->get_relativeVirtualAddress( &rvaLast ) == S_OK )  
    {  
        pSym = 0;  
        if ( FAILED( pEnumByAddr->symbolByRVA( rvaLast, &pSym ) ) )  
        {  
            Fatal( "symbolByAddr" );  
        }  
        printf( "Symbols in order\n" );  
        do  
        {   
            CDiaBSTR name;  
            if ( pSym->get_name( &name ) != S_OK )  
            {  
                printf( "\t0x%08X (%ws) <no name>\n", rvaLast );  
            }  
            else  
            {  
               printf( "\t0x%08X %ws\n", rvaLast, name );  
            }  
            pSym = 0;  
            celt = 0;  
            if ( FAILED( hr = pEnumByAddr->Next( 1, &pSym, &celt ) ) )  
            {  
                break;  
            }  
        } while ( celt == 1 );  
    }  
}  
```  
  
## <a name="requirements"></a>需求  
 標頭：dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>另請參閱  
 [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
