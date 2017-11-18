---
title: "Idiasymbol:: Get_haslongjump |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_hasLongJump method
ms.assetid: 14484cb1-43b0-47a1-a9a8-081b55566886
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f4f6c95cea5a0ff6231f57d6297384dee6ba847
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgethaslongjump"></a>IDiaSymbol::get_hasLongJump
擷取指定函式是否包含使用的旗標[longjmp](/cpp/c-runtime-library/reference/longjmp)命令 (搭配[setjmp](/cpp/c-runtime-library/reference/setjmp)命令時，這些形成例外狀況處理的 C 樣式方法)。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_hasLongJump  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pFlag`  
 [out]傳回`TRUE`函數若包含`longjmp`命令; 否則傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不是使用符號。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|版本:|DIA SDK v8.0|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Idiasymbol:: Get_hassetjump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)   
 [longjmp](/cpp/c-runtime-library/reference/longjmp)   
 [setjmp](/cpp/c-runtime-library/reference/setjmp)