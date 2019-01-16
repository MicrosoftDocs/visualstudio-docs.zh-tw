---
title: 'Idialinenumber:: Get_length |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_length method
ms.assetid: 2c55a6f7-4ef5-45fb-9fd1-d72deaaa2829
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 34e36486f95964169200cee7c41ac8eaebc27960
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916409"
---
# <a name="idialinenumbergetlength"></a>IDiaLineNumber::get_length
擷取在區塊中的位元組數目。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_length (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]在區塊中傳回位元組的數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 區塊是該行的原始碼的長度表示的[IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)物件。  
  
## <a name="see-also"></a>請參閱  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)