---
title: IDiaSymbol::get_acceleratorPointerTags |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efad3aeaf0d8a30d521d16612639d0b663ee8ebe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51720665"
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

傳回所有加速器指標的標記值對應至 c + + AMP 加速器虛設常式函式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>參數  
 `cnt`  
 [in]輸出陣列的大小`pPointerTags`。  
  
 `pcnt`  
 [out]在 c + + AMP 加速器虛設常式的函式中的加速器指標標記計數。  
  
 `pPointerTags`  
 [out]A`DWORD`加速器指標標記值，在 c + + AMP 加速器虛設常式的函式中會填入的陣列指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
## <a name="remarks"></a>備註  
 在呼叫這個方法`IDiaSymbol`對應至 c + + AMP 加速器虛設常式函式的介面。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



