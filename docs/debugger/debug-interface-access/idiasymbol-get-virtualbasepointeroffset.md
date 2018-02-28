---
title: "Idiasymbol:: Get_virtualbasepointeroffset |Microsoft 文件"
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
- IDiaSymbol::get_virtualBasePointerOffset method
ms.assetid: a4f2649c-6702-491c-90a1-d6d669258c51
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 71102411e3229db2cac61af097503f8a05c7ee8f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetvirtualbasepointeroffset"></a>IDiaSymbol::get_virtualBasePointerOffset
擷取虛擬基底指標的位移。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_virtualBasePointerOffset (   
   LONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回虛擬基底指標的位移。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不是使用符號。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)