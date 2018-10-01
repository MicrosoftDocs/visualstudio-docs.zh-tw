---
title: 'Idiasymbol:: Get_hassetjump |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSetJump method
ms.assetid: 22656206-dccf-40ed-b179-fc016d1b262a
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a87713d5e0a1fcbdfb7fbfc267696525eff1f2b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490741"
---
# <a name="idiasymbolgethassetjump"></a>IDiaSymbol::get_hasSetJump
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[idiasymbol:: Get_hassetjump](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-hassetjump)。  
  
擷取指定的函式是否包含使用的旗標[setjmp](http://msdn.microsoft.com/library/684a8b27-e8eb-455b-b4a8-733ca1cbd7d2)命令 (搭配[longjmp](http://msdn.microsoft.com/library/0e13670a-5130-45c1-ad69-6862505b7a2f)命令時，這些形成例外狀況處理的 C 樣式方法)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT get_hasSetJump(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pFlag`  
 [out]會傳回`TRUE`函數若包含`setjmp`命令; 否則會傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2.h|  
|版本:|DIA SDK 8.0 版|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Idiasymbol:: Get_haslongjump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)   
 [longjmp](http://msdn.microsoft.com/library/0e13670a-5130-45c1-ad69-6862505b7a2f)   
 [setjmp](http://msdn.microsoft.com/library/684a8b27-e8eb-455b-b4a8-733ca1cbd7d2)



