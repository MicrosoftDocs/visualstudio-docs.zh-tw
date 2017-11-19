---
title: "Idiastackframe:: Get_registervalue |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a454beb98fc8579bf625dbdb64db1cf60f8dd50a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiastackframegetregistervalue"></a>IDiaStackFrame::get_registerValue
儲存在堆疊框架中，擷取指定的暫存器的值。  
  
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
 如果成功，傳回`S_OK`，否則會傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [CV_HREG_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)