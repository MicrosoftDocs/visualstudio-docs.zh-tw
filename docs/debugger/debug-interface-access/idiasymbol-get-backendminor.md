---
title: 'Idiasymbol:: Get_backendminor |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndMinor method
ms.assetid: 37f38d19-6685-440d-a477-7127c4f8699e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d2470586e958017a660f7f7820d2d902213abb4e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53819805"
---
# <a name="idiasymbolgetbackendminor"></a>IDiaSymbol::get_backEndMinor
擷取後端的次要版本號碼的編譯器。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_backEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回的後端的次要版本號碼。 請參閱＜備註＞。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不是適用於符號。  
  
## <a name="remarks"></a>備註  
 編譯器通常由兩個主要項目所組成： 前端 （剖析器），以處理剖析原始程式碼以中繼形式和一個後端 （程式碼產生器），然後將中繼的形式轉換成組件。 您不可能發生的前端與後端的不同版本的狀況。  
  
 前端或後端版本號碼是三個部分組成：\<主要 >。\<次要 >。\<建置 >，其中\<主要 > 是主要版本號碼，\<次要 > 是次要版本號碼，以及\<建置 > 是的組建編號。 例如 13.10.3077。  
  
## <a name="requirements"></a>需求  
  
|需求|說明|  
|-----------------|-----------------|  
|標頭：|dia2.h|  
|版本:|DIA SDK v7.0|  
  
## <a name="see-also"></a>請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)