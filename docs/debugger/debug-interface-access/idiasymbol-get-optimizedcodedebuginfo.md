---
title: "Idiasymbol:: Get_optimizedcodedebuginfo |Microsoft 文件"
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
- IDiaSymbol::get_optimizedCodeDebugInfo method
ms.assetid: 57ef4170-37a9-46b0-8217-c1a674725113
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c0ae8a0ef1e088667f51fa2f5886601cc8ddfd25
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetoptimizedcodedebuginfo"></a>IDiaSymbol::get_optimizedCodeDebugInfo
擷取指出函數是否包含特定的最佳化程式碼偵錯資訊的旗標。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_optimizedCodeDebugInfo(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pFlag`  
 [out]傳回`TRUE`如果最佳化的函式或標籤包含偵錯資訊; 否則會傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不適用於符號。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2.h|  
  
## <a name="see-also"></a>請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)