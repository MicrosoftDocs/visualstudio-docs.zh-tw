---
title: "Idiasymbol:: Get_offset |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_offset method
ms.assetid: 8292bb08-4dc8-4663-beb4-258f5d5a448d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd3fa794da188e228f44b0930bcf5b27f4b3a0fb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetoffset"></a>IDiaSymbol::get_offset
擷取符號位置的位移。 使用時機[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)是`LocIsRegRel`或`LocIsBitField`。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_offset (   
   LONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回以位元組為單位的符號位置的位移。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不適用於符號。  
  
## <a name="remarks"></a>備註  
 此位移為從一些已知的起點，如上所述。 例如，位移`LocIsBitField`位置型別通常是從包含類別的開始。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|版本:|DIA SDK v7.0|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)