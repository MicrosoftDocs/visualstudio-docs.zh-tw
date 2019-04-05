---
title: IDiaFrameData | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData interface
ms.assetid: 2f1b4986-341b-4641-89a4-226e261e9d93
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9619d4f3d5670d3692c21d850201a2f39d96b922
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940686"
---
# <a name="idiaframedata"></a>IDiaFrameData
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

公開 （expose) 堆疊框架的詳細的資料。  
  
## <a name="syntax"></a>語法  
  
```  
IDiaFrameData : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDiaFrameData`。  
  
|方法|描述|  
|------------|-----------------|  
|[IDiaFrameData::get_addressSection](../../debugger/debug-interface-access/idiaframedata-get-addresssection.md)|擷取框架的程式碼位址中區段的一部分。|  
|[IDiaFrameData::get_addressOffset](../../debugger/debug-interface-access/idiaframedata-get-addressoffset.md)|擷取框架的程式碼位址位移的一部分。|  
|[IDiaFrameData::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiaframedata-get-relativevirtualaddress.md)|擷取的映像相對虛擬位址 (RVA) 框架的程式碼。|  
|[IDiaFrameData::get_virtualAddress](../../debugger/debug-interface-access/idiaframedata-get-virtualaddress.md)|擷取框架的程式碼的虛擬位址 (VA)。|  
|[IDiaFrameData::get_lengthBlock](../../debugger/debug-interface-access/idiaframedata-get-lengthblock.md)|擷取的長度，以位元組為單位的畫面格所描述的程式碼區塊。|  
|[IDiaFrameData::get_lengthLocals](../../debugger/debug-interface-access/idiaframedata-get-lengthlocals.md)|擷取推送到堆疊上的本機變數的位元組的數目。|  
|[IDiaFrameData::get_lengthParams](../../debugger/debug-interface-access/idiaframedata-get-lengthparams.md)|擷取位元組的推送到堆疊上的參數數目。|  
|[IDiaFrameData::get_maxStack](../../debugger/debug-interface-access/idiaframedata-get-maxstack.md)|擷取推入堆疊框架中的位元組的數目上限。|  
|[IDiaFrameData::get_lengthProlog](../../debugger/debug-interface-access/idiaframedata-get-lengthprolog.md)|擷取的初構程式碼區塊中的位元組數目。|  
|[IDiaFrameData::get_lengthSavedRegisters](../../debugger/debug-interface-access/idiaframedata-get-lengthsavedregisters.md)|擷取已儲存的暫存器推送到堆疊上的位元組數目。|  
|[IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)|擷取用來計算目前的函式的呼叫之前設定的暫存器的程式字串。|  
|[IDiaFrameData::get_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md)|擷取指出該系統例外狀況處理的旗標是作用中。|  
|[IDiaFrameData::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)|擷取指出該 c + + 例外狀況處理的旗標是作用中。|  
|[IDiaFrameData::get_functionStart](../../debugger/debug-interface-access/idiaframedata-get-functionstart.md)|擷取指出區塊包含函式的進入點的旗標。|  
|[IDiaFrameData::get_allocatesBasePointer](../../debugger/debug-interface-access/idiaframedata-get-allocatesbasepointer.md)|擷取指出基底的指標會配置此位址範圍中的程式碼的旗標。 這個方法已淘汰。|  
|[IDiaFrameData::get_type](../../debugger/debug-interface-access/idiaframedata-get-type.md)|擷取編緝器特定畫面格型別。|  
|[IDiaFrameData::get_functionParent](../../debugger/debug-interface-access/idiaframedata-get-functionparent.md)|擷取框架資料介面以提供封入函式。|  
|[IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)|執行堆疊回溯並傳回在堆疊查核行程框架介面中的暫存器的目前狀態。|  
  
## <a name="remarks"></a>備註  
 適用於框架的詳細資料適用於位址和區塊長度所指定的位址範圍內的執行點。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 取得這個介面，藉由呼叫[idiaenumframedata:: Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)或是[idiaenumframedata:: Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)方法。 請參閱[IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)介面，如需詳細資訊。  
  
## <a name="example"></a>範例  
 此範例會列印出的屬性`IDiaFrameData`物件。 請參閱[IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)介面，如需如何的範例`IDiaFrameData`介面取得。  
  
```cpp#  
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
 標頭：dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>另請參閱  
 [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)   
 [IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)
