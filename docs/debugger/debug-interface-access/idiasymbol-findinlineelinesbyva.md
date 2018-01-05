---
title: "IDiaSymbol::findInlineeLinesByVA |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 61427d33-30d2-4ac9-9bd6-c58c6c705072
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 912beca94c2575564bfa6634c8fc3c44ffb54456
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolfindinlineelinesbyva"></a>IDiaSymbol::findInlineeLinesByVA
擷取可讓用戶端來逐一查看的是內嵌的直接或間接，此符號內指定的虛擬位址 (VA) 中的所有函式的行號資訊的列舉。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT findInlineeLinesByVA (   
   ULONGLONG             va,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `va`  
 [in]指定的位址為 VA.  
  
 `length`  
 [in]指定的位址範圍，在與此查詢所涵蓋的位元組數目。  
  
 `ppResult`  
 [out]保存`IDiaEnumLineNumbers`物件，其中包含所擷取的行號的清單。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)