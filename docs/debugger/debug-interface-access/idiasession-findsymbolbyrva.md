---
title: 'Idiasession:: Findsymbolbyrva |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByRVA method
ms.assetid: 14fb2903-b771-44d6-b0a8-44e0097c58ce
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ef883d8b0aa7870b9444ea92f6b0b23143caf43d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53832962"
---
# <a name="idiasessionfindsymbolbyrva"></a>IDiaSession::findSymbolByRVA
擷取包含此項目，或指定相對虛擬位址 (RVA) 到最接近指定的符號類型。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT findSymbolByRVA (   
   DWORD        rva,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>參數  
 `rva`  
 [in]指定的 RVA。  
  
 `symtag`  
 [in]若要找的符號類型。 值取自[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)列舉型別。  
  
 `ppSymbol`  
 [out]傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)擷取表示符號的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="example"></a>範例  
  
```C++  
IDiaSymbol* pFunc;  
pSession->findSymbolByRVA( rva, SymTagFunction, &pFunc );  
```  
  
## <a name="see-also"></a>請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)