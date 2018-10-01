---
title: 'Idiasymbol:: Get_hasseh |Microsoft Docs'
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
- IDiaSymbol::get_hasSEH method
ms.assetid: 1a709ded-22c8-464c-97be-eba5e464210c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f8dd3eda1eaf992de0b38e26bde93ae3f4c1de05
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491534"
---
# <a name="idiasymbolgethasseh"></a>IDiaSymbol::get_hasSEH
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[idiasymbol:: Get_hasseh](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-hasseh)。  
  
擷取指定的函式是否包含任何的旗標[Structured Exception Handling （C/c + +）](http://msdn.microsoft.com/library/dd3b647d-c269-43a8-aab9-ad1458712976) (例如 __try /\__except 區塊)。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_hasSEH(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pFlag`  
 [out]會傳回`TRUE`函式有任何結構化的例外狀況處理區塊; 否則會傳回`FALSE`。  
  
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
 [結構化例外狀況處理 (C/C++)](http://msdn.microsoft.com/library/dd3b647d-c269-43a8-aab9-ad1458712976)



