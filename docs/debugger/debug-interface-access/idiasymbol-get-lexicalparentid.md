---
title: "Idiasymbol:: Get_lexicalparentid |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_lexicalParentId method
ms.assetid: 6c0c2874-cc47-4e4f-ad9c-02a18a108d9d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 680cd9aea768d29e2afa4295a9593279a67e6c63
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetlexicalparentid"></a>IDiaSymbol::get_lexicalParentId
擷取符號的語彙的父識別碼。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_lexicalParentId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回的符號的語彙的父識別碼。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不適用於符號。  
  
## <a name="remarks"></a>備註  
 識別碼是由 DIA SDK，以將標示為唯一的所有符號的唯一值。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)