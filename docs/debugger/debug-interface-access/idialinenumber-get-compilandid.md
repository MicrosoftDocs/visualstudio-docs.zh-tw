---
title: 'Idialinenumber:: Get_compilandid |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_compilandId method
ms.assetid: 2cd6f551-8091-47c7-803f-3f79a766a211
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc39924da691440d6fdffa59a744f5c3dd187568
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53843576"
---
# <a name="idialinenumbergetcompilandid"></a>IDiaLineNumber::get_compilandId
擷取提供這一行將編譯模組的唯一識別碼。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_compilandId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回`DWORD`包含提供這一行將編譯模組的唯一識別碼。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)