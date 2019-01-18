---
title: BasicType | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 891b83d6a43cb73fe8f38bb8b20201cbcfa230f6
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54154078"
---
# <a name="basictype"></a>BasicType
指定符號的基本類型。  
  
## <a name="syntax"></a>語法  
  
```C++  
enum BasicType {   
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
   btHresult  = 31,  
   btChar16   = 32,  // char16_t
   btChar32   = 33,  // char32_t
};  
```  
  
## <a name="elements"></a>項目  
 btNoType  
 未不指定任何基本的類型。  
  
 btVoid  
 基本類型是`void`。  
  
 btChar  
 基本類型是`char`（C/c + + 型別）。  
  
 btWChar  
 基本類型是寬 (Unicode) 字元 (`WCHAR`)。  
  
 btInt  
 基本類型是`signed int`（C/c + + 型別）。  
  
 btUInt  
 基本類型是`unsigned int`（C/c + + 型別）。  
  
 btFloat  
 基本的型別是浮點數 (`FLOAT`)。  
  
 btBCD  
 基本類型是二進位編碼的十進位 (`BCD`)。  
  
 btBool  
 基本的型別是布林值 (`BOOL`)。  
  
 btLong  
 基本類型是`long int`（C/c + + 型別）。  
  
 btULong  
 基本類型是`unsigned long int`（C/c + + 型別）。  
  
 btCurrency  
 基本類型為貨幣。  
  
 btDate  
 基本類型是日期/時間 (`DATE`)。  
  
 btVariant  
 基本的型別是一種變數類型結構 (`VARIANT`)。  
  
 btComplex  
 基本類型會是複數。  
  
 btBit  
 一些基本的類型。  
  
 btBSTR  
 基本的類型是基本或二進位字串 (`BSTR`)。  
  
 btHresult  
 基本類型是`HRESULT`。  
  
## <a name="remarks"></a>備註  
 傳回這個列舉型別中的值[idiasymbol:: Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： cvconst.h  
  
## <a name="see-also"></a>請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
