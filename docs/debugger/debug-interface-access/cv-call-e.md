---
title: "CV_call_e |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89340c4cd448201f7624f5ec6b15dc67f74db4f6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="cvcalle"></a>CV_call_e
指定的函式的呼叫慣例。  
  
> [!NOTE]
>  只有最常見的列舉值記載於此。 Cvconst.h 標頭檔中可完整列舉。  
  
## <a name="syntax"></a>語法  
  
```C++  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## <a name="elements"></a>項目  
 CV_CALL_NEAR_C  
 指定使用 near 由右至左推入函式呼叫慣例。 呼叫的函式會清除堆疊。  
  
 CV_CALL_NEAR_FAST  
 指定暫存器中使用 near 左到右推入函式呼叫慣例。 呼叫的函式會清除堆疊使用參數的位元組總數。  
  
 CV_CALL_NEAR_STD  
 指定使用 near 標準呼叫 （由右至左推入） 的函式呼叫慣例。  
  
 CV_CALL_NEAR_SYS  
 指定使用附近的系統呼叫的函式呼叫慣例。  
  
 CV_CALL_THISCALL  
 指定的函式呼叫慣例 using`this`呼叫 (`this`暫存器中傳遞指標)。  
  
 CV_CALL_CLRCALL  
 指定使用的 Common Language Runtime (CLR) （也稱為 managed 程式碼呼叫慣例） 函式呼叫慣例。  
  
## <a name="remarks"></a>備註  
 這個列舉型別中的值會傳回透過呼叫[idiasymbol:: Get_callingconvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： cvconst.h  
  
## <a name="see-also"></a>另請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)