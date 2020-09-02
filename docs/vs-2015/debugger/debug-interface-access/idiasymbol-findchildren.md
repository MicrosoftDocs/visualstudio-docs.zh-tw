---
title: IDiaSymbol：： findChildren |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150042"
---
# <a name="idiasymbolfindchildren"></a>IDiaSymbol::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取符號的子系。  
  
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
 在指定要抓取之子系的符號標記，如 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)中所定義。 `SymTagNull`針對要取出的所有子系，設定為。  
  
 `name`  
 在指定要抓取之子系的名稱。 `NULL`針對要取出的所有子系，設定為。  
  
 `compareFlags`  
 在指定套用至名稱比對的比較選項。 [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)列舉中的值可以單獨使用或合併使用。  
  
 `ppResult`  
 擴展傳回 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) 物件，其中包含已抓取之子符號的清單。  
  
## <a name="return-value"></a>傳回值  
 `S_OK`如果找到至少一個符號的子系，則會傳回 `S_FALSE` ; 如果找不到子系，則會傳回，否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法與使用此符號做為第一個參數來呼叫 [IDiaSession：： findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md) 方法相同。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession：： findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)
