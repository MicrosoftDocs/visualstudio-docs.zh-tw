---
title: 'Idiasymbol:: Get_isltcg |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isLTCG method
ms.assetid: 5f7f05b8-6b71-4958-9e1e-e4924ef9c59b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 33d3ea0720e7354cc50e77d555adc5af43ac9d96
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53831793"
---
# <a name="idiasymbolgetisltcg"></a>IDiaSymbol::get_isLTCG
擷取指定的旗標是否[編譯模組](../../debugger/debug-interface-access/compiland.md)已與連結器參數連結[/LTCG （連結時間程式碼產生）](/cpp/build/reference/ltcg-link-time-code-generation)，這可以協助整個程式最佳化。 這個參數只適用於 managed 程式碼。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_iSLTCG(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>參數  
 pFlag  
 [out]會傳回`TRUE`如果`compiland`/LTCG 連結器參數與已連結，否則會傳回`FALSE`。  
  
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