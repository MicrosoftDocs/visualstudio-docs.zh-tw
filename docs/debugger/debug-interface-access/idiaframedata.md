---
title: IDiaFrameData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData interface
ms.assetid: 2f1b4986-341b-4641-89a4-226e261e9d93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d586cfe3e78a320ffed42e7181463eb79a6b313a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743461"
---
# <a name="idiaframedata"></a>IDiaFrameData
公開堆疊框架的詳細資料。

## <a name="syntax"></a>語法

```
IDiaFrameData : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示 `IDiaFrameData` 的方法。

|方法|描述|
|------------|-----------------|
|[IDiaFrameData::get_addressSection](../../debugger/debug-interface-access/idiaframedata-get-addresssection.md)|抓取框架的程式碼位址區段部分。|
|[IDiaFrameData::get_addressOffset](../../debugger/debug-interface-access/idiaframedata-get-addressoffset.md)|抓取框架的程式碼位址位移部分。|
|[IDiaFrameData::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiaframedata-get-relativevirtualaddress.md)|抓取框架之程式碼的影像相對虛擬位址（RVA）。|
|[IDiaFrameData::get_virtualAddress](../../debugger/debug-interface-access/idiaframedata-get-virtualaddress.md)|抓取框架的程式碼虛擬位址（VA）。|
|[IDiaFrameData::get_lengthBlock](../../debugger/debug-interface-access/idiaframedata-get-lengthblock.md)|抓取框架所描述之程式碼區塊的長度（以位元組為單位）。|
|[IDiaFrameData::get_lengthLocals](../../debugger/debug-interface-access/idiaframedata-get-lengthlocals.md)|抓取推播于堆疊上的本機變數的位元組數目。|
|[IDiaFrameData::get_lengthParams](../../debugger/debug-interface-access/idiaframedata-get-lengthparams.md)|抓取堆疊上推送之參數的位元組數目。|
|[IDiaFrameData::get_maxStack](../../debugger/debug-interface-access/idiaframedata-get-maxstack.md)|抓取框架中堆疊推送的最大位元組數目。|
|[IDiaFrameData::get_lengthProlog](../../debugger/debug-interface-access/idiaframedata-get-lengthprolog.md)|抓取區塊中序言程式碼的位元組數目。|
|[IDiaFrameData::get_lengthSavedRegisters](../../debugger/debug-interface-access/idiaframedata-get-lengthsavedregisters.md)|抓取堆疊上推送之已儲存暫存器的位元組數目。|
|[IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)|抓取在呼叫目前的函式之前，用來計算暫存器集的程式字串。|
|[IDiaFrameData::get_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md)|抓取表示系統例外狀況處理已生效的旗標。|
|[IDiaFrameData::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)|抓取表示C++例外狀況處理作用中的旗標。|
|[IDiaFrameData::get_functionStart](../../debugger/debug-interface-access/idiaframedata-get-functionstart.md)|抓取旗標，指出區塊包含函數的進入點。|
|[IDiaFrameData::get_allocatesBasePointer](../../debugger/debug-interface-access/idiaframedata-get-allocatesbasepointer.md)|抓取表示基底指標已配置給此位址範圍內之程式碼的旗標。 此方法已淘汰。|
|[IDiaFrameData::get_type](../../debugger/debug-interface-access/idiaframedata-get-type.md)|捕獲編譯器特定的框架類型。|
|[IDiaFrameData::get_functionParent](../../debugger/debug-interface-access/idiaframedata-get-functionparent.md)|抓取封閉函數的框架資料介面。|
|[IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)|執行堆疊回溯，並傳回堆疊引導框架介面中暫存器的目前狀態。|

## <a name="remarks"></a>備註
 框架的詳細資料適用于位址範圍內的執行點，網址和區塊長度表示。

## <a name="notes-for-callers"></a>呼叫者的注意事項
 藉由呼叫[IDiaEnumFrameData：： Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)或[IDiaEnumFrameData：： Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)方法來取得此介面。 如需詳細資訊，請參閱[IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)介面。

## <a name="example"></a>範例
 這個範例會列印出 `IDiaFrameData` 物件的屬性。 如需如何取得 `IDiaFrameData` 介面的範例，請參閱[IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)介面。

```C++
void PrintFrameData(IDiaFrameData* pFrameData){
    DWORD dwSect;
    DWORD dwOffset;
    DWORD cbBlock;
    DWORD cbLocals; // Number of bytes reserved for the function locals
    DWORD cbParams; // Number of bytes reserved for the function arguments
    DWORD cbMaxStack;
    DWORD cbProlog;
    DWORD cbSavedRegs;
    BOOL  bSEH;
    BOOL  bEH;
    BOOL  bStart;
    BSTR  wszProgram;

    if(pFrameData->get_addressSection(&dwSect) == S_OK &&
       pFrameData->get_addressOffset(&dwOffset) == S_OK &&
       pFrameData->get_lengthBlock(&cbBlock) == S_OK &&
       pFrameData->get_lengthLocals(&cbLocals) == S_OK &&
       pFrameData->get_lengthParams(&cbParams) == S_OK &&
       pFrameData->get_maxStack(&cbMaxStack) == S_OK &&
       pFrameData->get_lengthProlog(&cbProlog) == S_OK &&
       pFrameData->get_lengthSavedRegisters(&cbSavedRegs) == S_OK &&
       pFrameData->get_systemExceptionHandling(&bSEH) == S_OK &&
       pFrameData->get_cplusplusExceptionHandling(&bEH) == S_OK &&
       pFrameData->get_functionStart(&bStart) == S_OK )
    {
        wprintf(L"Frame address  : %04X:%08X\n", dwSect, dwOffset);
        wprintf(L"Block size     : 0x%8X\n", cbBlock);
        wprintf(L"Locals size    : 0x%8X\n", cbLocals);
        wprintf(L"Parms size     : 0x%8X\n", cbParams);
        wprintf(L"Max stack used : 0x%8X\n", cbMaxStack);
        wprintf(L"Prolog size    : 0x%8X\n", cbProlog);
        wprintf(L"Saved regs size: 0x%8X\n", cbSavedRegs);
        wprintf(L"System Exception Handling: %c\n", bSEH ? L'Y' : L'N');
        wprintf(L"C++ Exception Handling   : %c\n", bEH ? L'Y' : L'N');
        wprintf(L"Function starts in block : %c\n", bStart ? L'Y' : L'N');

        if (pFrameData->get_program(&wszProgram) == S_OK)
        {
            wprintf(L"Program used for register set: %s\n", wszProgram);
            SysFreeString(wszProgram);
        }
        else
        {
            wprintf(L"\n");
        }
    }
}
```

## <a name="requirements"></a>需求
標頭： Dia2。h

程式庫： diaguids

DLL： msdia80

## <a name="see-also"></a>請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)
- [IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)
