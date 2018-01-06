---
title: "Idiasymbol:: Get_inlspec |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_InlSpec method
ms.assetid: 30af6a2f-be84-429e-a96a-d0f9ed9343fb
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fb8b96e3a44ae1bb03cde58fc28af4871e80aaf4
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="idiasymbolgetinlspec"></a>IDiaSymbol::get_InlSpec
此函式會擷取旗標，指出是否函式已標記為內嵌 (使用其中一種[inline、 __inline、 \__forceinline](/cpp/cpp/inline-functions-cpp)屬性)。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_inlSpec(  
   BOOL *pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回`TRUE`如果函式已標記為內嵌; 否則會傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不是使用符號。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2.h|  
|版本:|DIA SDK v8.0|  
  
## <a name="see-also"></a>請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [inline、__inline、\__forceinline](/cpp/cpp/inline-functions-cpp)