---
title: "IDiaSymbol::get_acceleratorPointerTags |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e5190496258cfb4ed66334e10a3d727a1c9555b6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
傳回所有 accelerator 指標的標記值對應至 c + + AMP 加速器虛設常式函式。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>參數  
 `cnt`  
 [in]輸出陣列的大小`pPointerTags`。  
  
 `pcnt`  
 [out]在 c + + AMP 加速器虛設常式函式中的對應鍵指標標記計數。  
  
 `pPointerTags`  
 [out]A`DWORD`填滿 accelerator 指標標記值，在 c + + AMP 加速器虛設常式函式中的陣列指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法會在呼叫`IDiaSymbol`對應至 c + + AMP 加速器虛設常式函式的介面。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)