---
title: BasicType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 38de89b9774ac20f67b91e4ba864534122f4cdb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580833"
---
# <a name="basictype"></a>BasicType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

指定符號的基本類型。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
   btHresult  = 31  
};  
```  
  
## <a name="elements"></a>元素  
 btNoType  
 未指定任何基本類型。  
  
 btVoid  
 基本類型為 `void` 。  
  
 btChar  
 基本類型是 `char`)  (C/c + + 類型。  
  
 btWChar  
 Basic 型別是一種寬 (Unicode) 字元 (`WCHAR`) 。  
  
 btInt  
 基本類型是 `signed int` C/c + + 類型)  (。  
  
 btUInt  
 基本類型是 `unsigned int` C/c + + 類型)  (。  
  
 btFloat  
 基本類型是 () 的浮點數 `FLOAT` 。  
  
 btBCD  
 基本類型是二進位編碼的十進位 (`BCD`) 。  
  
 btBool  
 基本類型是 () 的布林值 `BOOL` 。  
  
 btLong  
 基本類型是 `long int`)  (C/c + + 類型。  
  
 btULong  
 基本類型是 `unsigned long int`)  (C/c + + 類型。  
  
 btCurrency  
 基本類型為 currency。  
  
 btDate  
 基本類型是日期/時間 (`DATE`) 。  
  
 btVariant  
 基本類型是)  (變數類型結構 `VARIANT` 。  
  
 btComplex  
 基本類型是複數。  
  
 btBit  
 基本類型是 bit。  
  
 btBSTR  
 基本類型是 () 的基本或二進位字串 `BSTR` 。  
  
 btHresult  
 基本類型為 `HRESULT` 。  
  
## <a name="remarks"></a>備註  
 [IDiaSymbol：： get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)方法會傳回這個列舉中的值。  
  
## <a name="requirements"></a>需求  
 標頭： cvconst。h  
  
## <a name="see-also"></a>另請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol：： get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
