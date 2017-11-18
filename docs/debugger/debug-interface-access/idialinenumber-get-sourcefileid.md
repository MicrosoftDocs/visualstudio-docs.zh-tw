---
title: "Idialinenumber:: Get_sourcefileid |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLineNumber::get_sourceFileId method
ms.assetid: 4f482a1e-e85f-4173-98de-8e5f7622554b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26ad1cb7faeca9ef2aeadf15389c79815e23e893
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idialinenumbergetsourcefileid"></a>IDiaLineNumber::get_sourceFileId
擷取造成這一行的原始程式檔的唯一的來源檔案識別碼。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_sourceFileId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回造成這一行的原始程式檔的唯一來源檔案識別碼。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)