---
title: 'Idiastackframe:: Get_registervalue |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b0bb8f3a10bebbdaff489b2b628af2e1228fdf40
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985796"
---
# <a name="idiastackframegetregistervalue"></a>IDiaStackFrame::get_registerValue
擷取的值指定的暫存器儲存在堆疊框架中。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_registerValue(  
   ULONG      registerIndex,  
   ULONGLONG *pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `registerIndex`  
 [in]其中一個[CV_HREG_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)列舉值。  
  
 `pRetVal`  
 [out]在登錄中儲存的值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`，否則會傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [CV_HREG_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)