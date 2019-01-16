---
title: 'Idiasymbol:: Get_nostackordering |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_noStackOrdering method
ms.assetid: a1753917-705b-4165-9880-d05e91e6dcb4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6b9f570c6ae2e101e319d9789c7e8c7d391008c8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53963585"
---
# <a name="idiasymbolgetnostackordering"></a>IDiaSymbol::get_noStackOrdering
此函式會擷取指出是否沒有堆疊順序可以完成在堆疊緩衝區檢查的旗標 ([/GS （緩衝區安全性檢查）](/cpp/build/reference/gs-buffer-security-check)編譯器選項)。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_noStackOrdering(  
   BOOL *pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]會傳回`TRUE`沒有堆疊順序無法完成在堆疊緩衝區檢查; 否則會傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不是適用於符號。  
  
## <a name="requirements"></a>需求  
  
|需求|說明|  
|-----------------|-----------------|  
|標頭：|dia2.h|  
|版本:|DIA SDK 8.0 版|  
  
## <a name="see-also"></a>請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [/GS (緩衝區安全性檢查)](/cpp/build/reference/gs-buffer-security-check)