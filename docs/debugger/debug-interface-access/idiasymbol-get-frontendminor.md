---
title: "Idiasymbol:: Get_frontendminor |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_frontEndMinor method
ms.assetid: 40792153-827c-4859-be7c-6aa16d5abab6
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30bfe092ed8454b14a7e26d77b375c75cabc0836
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetfrontendminor"></a>IDiaSymbol::get_frontEndMinor
擷取前端次要版本號碼。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_frontEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回 front.end 次要版本號碼。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不適用於符號。  
  
## <a name="remarks"></a>備註  
 編譯器通常由兩個主要項目所組成： 前端 （剖析器），用來處理來源的程式碼剖析為中繼格式，以及的後端 （程式碼產生器），它會將中繼格式轉換成組件。 是很常見的前端有後端的版本不同的位置。  
  
 前端或後端版本號碼是三個部分組成：\<主要 >。\<次要 >。\<建置 >，其中\<主要 > 是主要版本號碼，\<次要 > 是次要版本號碼，和\<建置 > 是的組建編號。 例如，13.10.3077。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|版本:|DIA SDK v7.0|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)