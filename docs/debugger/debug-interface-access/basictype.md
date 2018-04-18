---
title: BasicType |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: df12ce7ff026215e7051142c2cbba47cb82ffc25
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="basictype"></a>BasicType
指定符號的基本類型。  
  
## <a name="syntax"></a>語法  
  
```C++  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## <a name="elements"></a>項目  
 btNoType  
 未不指定任何基本類型。  
  
 btVoid  
 基本類型是`void`。  
  
 btChar  
 基本類型是`char`（C/c + + 型別）。  
  
 btWChar  
 基本類型是寬的 (Unicode) 字元 (`WCHAR`)。  
  
 btInt  
 基本類型是`signed int`（C/c + + 型別）。  
  
 btUInt  
 基本類型是`unsigned int`（C/c + + 型別）。  
  
 btFloat  
 基本類型是浮點數 (`FLOAT`)。  
  
 btBCD  
 基本類型是二進位編碼的十進位 (`BCD`)。  
  
 btBool  
 基本類型為布林值 (`BOOL`)。  
  
 btLong  
 基本類型是`long int`（C/c + + 型別）。  
  
 btULong  
 基本類型是`unsigned long int`（C/c + + 型別）。  
  
 btCurrency  
 基本類型為貨幣。  
  
 btDate  
 基本類型是日期/時間 (`DATE`)。  
  
 btVariant  
 基本類型是一種變數型別結構 (`VARIANT`)。  
  
 btComplex  
 基本類型為複數。  
  
 btBit  
 基本類型為位元。  
  
 btBSTR  
 基本類型是基本或二進位字串 (`BSTR`)。  
  
 btHresult  
 基本類型是`HRESULT`。  
  
## <a name="remarks"></a>備註  
 所傳回的值，這個列舉型別中[idiasymbol:: Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： cvconst.h  
  
## <a name="see-also"></a>另請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasymbol:: Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)