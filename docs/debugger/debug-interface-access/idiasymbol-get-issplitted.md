---
title: 'Idiasymbol:: Get_issplitted |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isSplitted method
ms.assetid: ff160cf6-003b-4ef5-a406-20a7b287b2bf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 15c30577900a2d2e192bdc2dea45fc89846b102b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919323"
---
# <a name="idiasymbolgetissplitted"></a>IDiaSymbol::get_isSplitted
擷取指定資料符號是否已分割成彙總或其他符號; 集合的旗標編譯器會將符號視為個別的實體，即使它們實際上是較大的符號的一部分。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_isSplitted(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pFlag`  
 [out]會傳回`TRUE`符號已經分割成彙總的符號; 否則會傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。  
  
## <a name="remarks"></a>備註  
 [Idiasymbol:: Get_isaggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)方法會傳回`TRUE`屬於分割符號的所有符號。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2.h|  
|版本:|DIA SDK 8.0 版|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)