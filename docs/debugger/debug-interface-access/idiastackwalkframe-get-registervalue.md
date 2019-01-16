---
title: 'Idiastackwalkframe:: Get_registervalue |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::get_registerValue method
ms.assetid: ca3c20a9-934a-4b2c-a7f6-7d06e8611ff2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 78c80d0dbe682a511b209a0d357cb2fbf8f3fcf0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53961383"
---
# <a name="idiastackwalkframegetregistervalue"></a>IDiaStackWalkFrame::get_registerValue
擷取暫存器的值。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `index`  
 [in]值，以從[CV_HREG_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)指定註冊，即可取得其值的列舉類型。  
  
 `pRetVal`  
 [out]傳回目前的暫存器值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [CV_HREG_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)