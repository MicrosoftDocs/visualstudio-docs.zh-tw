---
title: IDiaLineNumber | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber interface
ms.assetid: 1071f7d0-1f8c-4384-933f-c49c7eb930bd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 62552c6cce3c17da52de14669071bec43db548de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864702"
---
# <a name="idialinenumber"></a>IDiaLineNumber
存取描述從影像文字位元組區塊對應至原始程式檔行號之進程的資訊。

## <a name="syntax"></a>Syntax

```
IDiaLineNumber : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示的方法 `IDiaLineNumber` 。

|方法|描述|
|------------|-----------------|
|[IDiaLineNumber::get_compiland](../../debugger/debug-interface-access/idialinenumber-get-compiland.md)|抓取編譯單位的符號參考，以提供影像文字的位元組。|
|[IDiaLineNumber::get_sourceFile](../../debugger/debug-interface-access/idialinenumber-get-sourcefile.md)|抓取來源檔案物件的參考。|
|[IDiaLineNumber::get_lineNumber](../../debugger/debug-interface-access/idialinenumber-get-linenumber.md)|捕獲原始程式檔中的行號。|
|[IDiaLineNumber::get_lineNumberEnd](../../debugger/debug-interface-access/idialinenumber-get-linenumberend.md)|抓取語句或運算式結束時，以一為基礎的來源行號。|
|[IDiaLineNumber::get_columnNumber](../../debugger/debug-interface-access/idialinenumber-get-columnnumber.md)|抓取運算式或語句開始的資料行編號。|
|[IDiaLineNumber::get_columnNumberEnd](../../debugger/debug-interface-access/idialinenumber-get-columnnumberend.md)|抓取運算式或語句結束的資料行編號。|
|[IDiaLineNumber::get_addressSection](../../debugger/debug-interface-access/idialinenumber-get-addresssection.md)|抓取區塊開始之記憶體位址的區段部分。|
|[IDiaLineNumber::get_addressOffset](../../debugger/debug-interface-access/idialinenumber-get-addressoffset.md)|抓取區塊開始之記憶體位址的位移部分。|
|[IDiaLineNumber::get_relativeVirtualAddress](../../debugger/debug-interface-access/idialinenumber-get-relativevirtualaddress.md)|抓取區塊 (RVA) 的影像相對虛擬位址。|
|[IDiaLineNumber::get_virtualAddress](../../debugger/debug-interface-access/idialinenumber-get-virtualaddress.md)|抓取區塊 (VA) 的虛擬位址。|
|[IDiaLineNumber::get_length](../../debugger/debug-interface-access/idialinenumber-get-length.md)|捕獲區塊中的位元組數目。|
|[IDiaLineNumber::get_sourceFileId](../../debugger/debug-interface-access/idialinenumber-get-sourcefileid.md)|抓取提供此行之原始程式檔的唯一來源檔案識別碼。|
|[IDiaLineNumber::get_statement](../../debugger/debug-interface-access/idialinenumber-get-statement.md)|抓取旗標，指出這行資訊描述程式來源中的語句開頭。|
|[IDiaLineNumber::get_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|抓取提供此行的編譯單位唯一識別碼。|

## <a name="remarks"></a>備註

## <a name="notes-for-callers"></a>呼叫者注意事項
藉由呼叫 [IDiaEnumLineNumbers：： Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md) 或 [IDiaEnumLineNumbers：： Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md) 方法來取得這個介面。

## <a name="example"></a>範例
下列函式會顯示函式中所使用的行號 (由 `pSymbol`) 表示。

```C++
void dumpFunctionLines( IDiaSymbol* pSymbol, IDiaSession* pSession )
{
    ULONGLONG length = 0;
    DWORD     isect  = 0;
    DWORD     offset = 0;

    pSymbol->get_addressSection( &isect );
    pSymbol->get_addressOffset( &offset );
    pSymbol->get_length( &length );
    if ( isect != 0 && length > 0 )
    {
        CComPtr< IDiaEnumLineNumbers > pLines;
        if ( SUCCEEDED( pSession->findLinesByAddr(
                                      isect,
                                      offset,
                                      static_cast<DWORD>( length ),
                                      &pLines)
                      )
           )
        {
            CComPtr< IDiaLineNumber > pLine;
            DWORD celt      = 0;
            bool  firstLine = true;

            while ( SUCCEEDED( pLines->Next( 1, &pLine, &celt ) ) &&
                    celt == 1 )
            {
                DWORD offset;
                DWORD seg;
                DWORD linenum;
                CComPtr< IDiaSymbol >     pComp;
                CComPtr< IDiaSourceFile > pSrc;

                pLine->get_compiland( &pComp );
                pLine->get_sourceFile( &pSrc );
                pLine->get_addressSection( &seg );
                pLine->get_addressOffset( &offset );
                pLine->get_lineNumber( &linenum );
                printf( "\tline %d at 0x%x:0x%x\n", linenum, seg, offset );
                pLine = NULL;
                if ( firstLine )
                {
                    // sanity check
                    CComPtr< IDiaEnumLineNumbers > pLinesByLineNum;
                    if ( SUCCEEDED( pSession->findLinesByLinenum(
                                                  pComp,
                                                  pSrc,
                                                  linenum,
                                                  0,
                                                  &pLinesByLineNum)
                                  )
                       )
                    {
                        CComPtr< IDiaLineNumber > pLine;
                        DWORD celt;
                        while ( SUCCEEDED( pLinesByLineNum->Next( 1, &pLine, &celt ) ) &&
                                celt == 1 )
                        {
                            DWORD offset;
                            DWORD seg;
                            DWORD linenum;

                            pLine->get_addressSection( &seg );
                            pLine->get_addressOffset( &offset );
                            pLine->get_lineNumber( &linenum );
                            printf( "\t\tfound line %d at 0x%x:0x%x\n", linenum, seg, offset );
                            pLine = NULL;
                        }
                    }
                    firstLine = false;
                }
            }
        }
    }
}
```

## <a name="requirements"></a>規格需求
標頭： Dia2。h

程式庫： diaguids .lib

DLL： msdia80.dll

## <a name="see-also"></a>另請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaEnumLineNumbers::Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md)
- [IDiaEnumLineNumbers::Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md)
