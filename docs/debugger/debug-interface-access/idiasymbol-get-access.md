---
title: "Idiasymbol:: Get_access |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_access method
ms.assetid: 908976ae-95c4-4020-89c9-de137f727f98
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 872478d4b94710bc994022ca19f5f913ce2368ea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetaccess"></a>IDiaSymbol::get_access
擷取的類別成員的存取修飾詞。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_access (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回值，從[CV_access_e 列舉](../../debugger/debug-interface-access/cv-access-e.md)列舉，指定類別成員的存取修飾詞。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不是使用符號。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|版本:|DIA SDK v7.0|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CV_access_e 列舉](../../debugger/debug-interface-access/cv-access-e.md)