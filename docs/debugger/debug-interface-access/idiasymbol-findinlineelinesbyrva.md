---
title: "IDiaSymbol::findInlineeLinesByRVA |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: ac108db1-9dbf-4dc4-bf48-159ca8d3725c
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed9a9fa2261ff034d7e2c870d4ee9fc557a39e47
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolfindinlineelinesbyrva"></a>IDiaSymbol::findInlineeLinesByRVA
擷取可讓用戶端來逐一查看的是內嵌的直接或間接指定相對的虛擬位址 (RVA) 中的這個符號中的所有函式的行號資訊的列舉。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT findInlineeLinesByRVA (    DWORD                 rva,   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `rva`  
 [in]指定的位址為 RVA。  
  
 `length`  
 [in]指定的位址範圍，在與此查詢所涵蓋的位元組數目。  
  
 `ppResult`  
 [out]保存`IDiaEnumLineNumbers`物件，其中包含所擷取的行號的清單。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)