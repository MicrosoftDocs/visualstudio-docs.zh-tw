---
title: 'Idialinenumber:: Get_sourcefileid |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_sourceFileId method
ms.assetid: 4f482a1e-e85f-4173-98de-8e5f7622554b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7d5376e0822d45bcfff238235e5256c484f48e29
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53837767"
---
# <a name="idialinenumbergetsourcefileid"></a>IDiaLineNumber::get_sourceFileId
擷取提供這行的原始程式檔的唯一的來源檔案識別碼。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_sourceFileId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回提供這行的原始程式檔的唯一來源檔案識別碼。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)