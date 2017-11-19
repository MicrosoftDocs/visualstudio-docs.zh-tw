---
title: "IDiaSymbol::get_isHLSLData |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 4662058b-c505-4ccf-ae03-739a62c814ca
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38c23148b717ba96ec934d4dc81cade0a9a81794
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetishlsldata"></a>IDiaSymbol::get_isHLSLData
指定這個符號表示高等級著色器語言 」 (HLSL) 資料。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_isHLSLData(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]指標`BOOL`，指定這個符號表示 HLSL 資料。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)