---
title: 'Idiaframedata:: Get_systemexceptionhandling |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_systemExceptionHandling method
ms.assetid: e8df1972-913c-446c-9779-775575b0caa9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf18ed2bb25ab2632c471c0da7d19ea54239c70d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53939936"
---
# <a name="idiaframedatagetsystemexceptionhandling"></a>IDiaFrameData::get_systemExceptionHandling
擷取指出系統例外狀況處理是否作用中的旗標。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_systemExceptionHandling (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 pRetVal  
 [out]會傳回`TRUE`如果系統例外狀況處理為作用中; 否則傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 系統例外狀況處理更常稱為結構化例外狀況處理。  
  
 若要判斷是否 c + + 例外狀況處理作用中，請呼叫[idiaframedata:: Get_cplusplusexceptionhandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)方法。  
  
## <a name="see-also"></a>請參閱  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)