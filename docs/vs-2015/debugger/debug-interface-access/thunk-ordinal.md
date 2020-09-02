---
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b98098c0b6e1de9c3c2ceda5c644bc2957ab22bd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62576404"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

指定 Thunk 類型。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
typedef enum THUNK_ORDINAL {   
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
  
## <a name="elements"></a>元素  
 THUNK_ORDINAL_NOTYPE  
 標準 Thunk。  
  
 THUNK_ORDINAL_ADJUSTOR  
 `this`Adjustor Thunk。  
  
 THUNK_ORDINAL_VCALL  
 虛擬呼叫 Thunk。  
  
 THUNK_ORDINAL_PCODE  
 P-code Thunk。  
  
 THUNK_ORDINAL_LOAD  
 延遲載入 Thunk。  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 累加式 trampoline Thunk (trampoline Thunk 是用來將呼叫從某個記憶體空間彈跳至另一個) 。  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 分支點 trampoline Thunk。  
  
## <a name="remarks"></a>備註  
 此列舉中的值會從 [IDiaSymbol：： get_ThunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) 方法的呼叫傳回。  
  
## <a name="requirements"></a>需求  
 標頭： cvconst。h  
  
## <a name="see-also"></a>另請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
