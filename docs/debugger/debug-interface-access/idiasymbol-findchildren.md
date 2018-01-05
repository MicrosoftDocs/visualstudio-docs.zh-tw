---
title: "Idiasymbol:: Findchildren |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::findChildren method
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 55be7f0acf312ad6fde5a0aee9214db27cd48088
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolfindchildren"></a>IDiaSymbol::findChildren
擷取符號的子系。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT findChildren (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `symtag`  
 [in]指定要擷取的子系的符號標記中所定義[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)。 設定為`SymTagNull`要擷取的所有子系。  
  
 `name`  
 [in]指定要擷取的子系的名稱。 設定為`NULL`要擷取的所有子系。  
  
 `compareFlags`  
 [in]指定套用至名稱比對的比較選項。 從數值[NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)列舉型別可以單獨或合併使用。  
  
 `ppResult`  
 [out]傳回[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)擷取物件，包含子符號清單。  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`符號的至少一個子系已找到，則會傳回`S_FALSE`如果找不到沒有子系; 否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法相當於呼叫[idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)完成這個符號的第一個參數的方法。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [Idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)