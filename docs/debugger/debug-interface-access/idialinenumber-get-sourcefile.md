---
title: 'Idialinenumber:: Get_sourcefile |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_sourceFile method
ms.assetid: 86fc4411-375e-4b99-8f96-4da2c3f68190
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf68651cf94341176de6c15b704a22d291d6dd12
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872296"
---
# <a name="idialinenumbergetsourcefile"></a>IDiaLineNumber::get_sourceFile
擷取來源檔案的參考。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_sourceFile (   
   IDiaSourceFile** pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)代表原始程式檔的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)