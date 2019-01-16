---
title: 'Idiaframedata:: Get_cplusplusexceptionhandling |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_cplusplusExceptionHandling method
ms.assetid: 54ee9cde-ce8e-45f1-809c-6fbad800d850
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2b7ceb69e4d4310330ea356037b7b155ea81f26
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959155"
---
# <a name="idiaframedatagetcplusplusexceptionhandling"></a>IDiaFrameData::get_cplusplusExceptionHandling
擷取指出 c + + 例外狀況處理是否作用中的旗標。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_cplusplusExceptionHandling (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]會傳回`TRUE`如果 c + + 例外狀況處理為作用中; 否則傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 判斷結構化例外處理是否作用中 （這是非常不同於 c + + 例外狀況處理），請呼叫[idiaframedata:: Get_systemexceptionhandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md)方法。  
  
## <a name="see-also"></a>請參閱  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md)