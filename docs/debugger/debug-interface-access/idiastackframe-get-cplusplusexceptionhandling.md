---
title: 'Idiastackframe:: Get_cplusplusexceptionhandling |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_cplusplusExceptionHandling method
ms.assetid: f2631820-c986-40ca-b61e-230d7a9c426c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 98047835046342731d5c04f0370b5b1be37ac8c6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889498"
---
# <a name="idiastackframegetcplusplusexceptionhandling"></a>IDiaStackFrame::get_cplusplusExceptionHandling
擷取指出 c + + 例外狀況處理是否作用中的旗標。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_cplusplusExceptionHandling (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]會傳回`TRUE`c + + 例外狀況處理實際上是這個框架中; 否則會傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`不支援的屬性。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 C + + 例外狀況處理不是結構化與相同或系統例外狀況處理。  
  
 若要判斷如果結構化例外狀況處理為作用中，請呼叫[IDiaStackFrame::get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md)方法。  
  
## <a name="see-also"></a>請參閱  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackFrame::get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md)