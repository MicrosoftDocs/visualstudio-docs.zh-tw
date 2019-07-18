---
title: 'Idiasymbol:: Findchildren |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildren method
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a09a62a2e6b94dbccda3afce4bdd286270149c15
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "68150042"
---
# <a name="idiasymbolfindchildren"></a>IDiaSymbol::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取之符號的子系。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT findChildren (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `symtag`  
 [in]指定要擷取的子系的符號標記中定義[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)。 若要設定`SymTagNull`要擷取的所有子系。  
  
 `name`  
 [in]指定要擷取的子系的名稱。 若要設定`NULL`要擷取的所有子系。  
  
 `compareFlags`  
 [in]指定比較選項套用至對應的名稱。 從數值[NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)單獨或合併，就可以使用列舉型別。  
  
 `ppResult`  
 [out]傳回[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)擷取物件，其中包含一份子符號。  
  
## <a name="return-value"></a>傳回值  
 會傳回`S_OK`如果找不到，至少一個子系的符號，或是傳回`S_FALSE`如果找不到任何子系; 否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法相當於呼叫[idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)完成這個符號的第一個參數的方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)
