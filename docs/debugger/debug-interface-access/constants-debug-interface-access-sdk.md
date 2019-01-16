---
title: 常數 （偵錯介面存取 SDK） |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdc54e15014e05f539c115675a97690e685cb5f1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852056"
---
# <a name="constants-debug-interface-access-sdk"></a>常數 (偵錯介面存取 SDK)
這些字串常數可用來識別不同的區段，透過 DIA SDK 的程式偵錯資料庫 (PDB) 檔。  
  
## <a name="constants"></a>常數  
 以下被宣告為 C/c + + 巨集。  
  
|巨集|值|  
|-----------|-----------|  
|`DiaTable_Symbols`|L 「 符號 」|  
|`DiaTable_Sections`|L 「 區段 」|  
|`DiaTable_SrcFiles`|L"SourceFiles 」|  
|`DiaTable_LineNums`|L"LineNumbers 」|  
|`DiaTable_SegMap`|L"SegmentMap 」|  
|`DiaTable_Dbg`|L"Dbg"|  
|`DiaTable_InjSrc`|L"InjectedSource 」|  
|`DiaTable_FrameData`|L"FrameData 」|  
  
## <a name="example"></a>範例  
 以下是使用其中一個這些符號的範例：  
  
```C++  
HRESULT GetSymbolTable(IDiaEnumTables *pEnumTables, IDiaTable **pTable)  
{  
    HRESULT hr;  
    VARIANT var;  
    var.vt      = VT_BSTR;  
    var.bstrVal = SysAllocString( DiaTable_Symbols );  
    hr = pEnumTables->Item( var, pTable );  
    return(hr);  
}  
```  
  
## <a name="requirements"></a>需求  
 標頭： dia2.h  
  
## <a name="see-also"></a>請參閱  
 [參考](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)