---
title: "IDiaSymbol::get_isOptimizedAway |Microsoft 文件"
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
ms.assetid: c18b1e38-b152-4a13-aba0-59faded5b2e6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4affd9883edece32317b40a6b985a6d8c0873a0f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetisoptimizedaway"></a>IDiaSymbol::get_isOptimizedAway
指定是否要立即最佳化變數。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_isOptimizedAway(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]指標`BOOL`，指定是否要立即最佳化變數。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)