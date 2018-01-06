---
title: "THUNK_ORDINAL |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0911b01bf52bd73cd438be024dab2580c5a94d1f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
將指定的 thunk 型別。  
  
## <a name="syntax"></a>語法  
  
```C++  
typedef enum THUNK_ORDINAL {   
   THUNK_ORDINAL_NOTYPE,  
   THUNK_ORDINAL_ADJUSTOR,  
   THUNK_ORDINAL_VCALL,  
   THUNK_ORDINAL_PCODE,  
   THUNK_ORDINAL_LOAD   
  
   // trampoline thunk ordinals - only for use in Trampoline thunk symbols  
   THUNK_ORDINAL_TRAMP_INCREMENTAL,  
   THUNK_ORDINAL_TRAMP_BRANCHISLAND,  
} THUNK_ORDINAL;  
```  
  
## <a name="elements"></a>項目  
 THUNK_ORDINAL_NOTYPE  
 標準的 thunk。  
  
 THUNK_ORDINAL_ADJUSTOR  
 A `this` adjustor thunk。  
  
 THUNK_ORDINAL_VCALL  
 虛擬呼叫 thunk。  
  
 THUNK_ORDINAL_PCODE  
 P 程式碼 thunk。  
  
 THUNK_ORDINAL_LOAD  
 延遲載入 thunk。  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 累加 trampoline thunk （trampoline thunk 用來從一個記憶體空間的呼叫跳躍到另一個）。  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 分支點 trampoline thunk。  
  
## <a name="remarks"></a>備註  
 這個列舉型別中的值會傳回呼叫[idiasymbol:: Get_thunkordinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： cvconst.h  
  
## <a name="see-also"></a>請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)