---
title: "IDiaSymbol::findChildrenExByAddr |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::findChildrenExByAddr
ms.assetid: c1e7885d-2d15-4529-9ac2-32dd22efe31c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8f5dbd7a6ad06ba10690e92042c9722eca5c99e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolfindchildrenexbyaddr"></a>IDiaSymbol::findChildrenExByAddr
擷取在指定的位址是有效的符號的子系。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT findChildrenExByAddr (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `symtag`  
 [in]指定要擷取的子系的符號標記中所定義[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)。 設定為`SymTagNull`要擷取的所有子系。  
  
 `name`  
 [in]指定要擷取的子系的名稱。 設定為`NULL`要擷取的所有子系。  
  
 `compareFlags`  
 [in]指定要套用至名稱比對的比較選項。 從數值[NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)列舉型別可以單獨或合併使用。  
  
 `address`  
 [in]符號的位址。  
  
 `ppResult`  
 [out]傳回[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)擷取物件，包含子符號清單。  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`符號的至少一個子系已找到，則會傳回`S_FALSE`如果找不到沒有子系; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 傳回的本機符號包含即時範圍資訊。  
  
## <a name="requirements"></a>需求  
 標頭： Dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [Idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)