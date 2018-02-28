---
title: "Idiasymbol:: Get_issafebuffers |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isSafeBuffers method
ms.assetid: f29e373d-e7bb-4181-ab9f-bf708d401d83
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5d5d311802101d632532ec1599ef39aff4a43141
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetissafebuffers"></a>IDiaSymbol::get_isSafeBuffers
擷取旗標，指定是否使用安全緩衝區中的前置指示詞。 使用時機[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)設`SymTagFunction`。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_isSafeBuffers(   
   BOOL* pRetVal)  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回`TRUE`如果指標會使用前置處理器指示詞的安全緩衝區; 否則傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不適用於符號。  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 標頭： Dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [strict_gs_check](/cpp/preprocessor/strict-gs-check)