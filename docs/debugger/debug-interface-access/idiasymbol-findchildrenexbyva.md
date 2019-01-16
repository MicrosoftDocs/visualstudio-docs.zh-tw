---
title: IDiaSymbol::findChildrenExByVA |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByVA
ms.assetid: 29080009-36e4-4697-acd7-50f2e3e1bf1b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b9a3f790acd7a285468810f981fd7e0210563eb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931138"
---
# <a name="idiasymbolfindchildrenexbyva"></a>IDiaSymbol::findChildrenExByVA
擷取在指定的虛擬位址是有效的符號的子系。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT findChildrenExByVA (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `symtag`  
 [in]指定要擷取的子系的符號標記中定義[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)。 若要設定`SymTagNull`要擷取的所有子系。  
  
 `name`  
 [in]指定要擷取的子系的名稱。 若要設定`NULL`要擷取的所有子系。  
  
 `compareFlags`  
 [in]指定要套用至名稱比對的比較選項。 從數值[NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)單獨或合併，就可以使用列舉型別。  
  
 `address`  
 [in]指定的虛擬位址。  
  
 `ppResult`  
 [out]傳回[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)擷取物件，其中包含一份子符號。  
  
## <a name="return-value"></a>傳回值  
 會傳回`S_OK`如果找不到，至少一個子系的符號，或是傳回`S_FALSE`找不到任何子系; 否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 會傳回本機符號包括即時範圍資訊。  
  
## <a name="requirements"></a>需求  
 標頭：dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)