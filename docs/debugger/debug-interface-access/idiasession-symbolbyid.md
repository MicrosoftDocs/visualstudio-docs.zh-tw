---
title: 'Idiasession:: Symbolbyid |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b4cafc8bf83c9c5e3a61712b6a3791bc234102c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
擷取符號依其唯一的識別項。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT symbolById (   
   DWORD        id,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>參數  
 `id`  
 [in]唯一識別項。  
  
 `ppSymbol`  
 [out]傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)擷取表示符號的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 指定的識別項是由 DIA SDK 在內部用來使所有符號都是唯一的唯一值。  
  
 這個方法可用，例如，擷取代表類型的另一個符號的符號 （請參閱範例）。  
  
## <a name="example"></a>範例  
 這個範例會擷取[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)代表類型的另一個符號。 這個範例示範如何使用`symbolById`工作階段中的方法。 更簡單的方法是呼叫[idiasymbol:: Get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)方法來直接擷取類型符號。  
  
```C++  
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)  
{  
    IDiaSymbol *pTypeSymbol = NULL;  
    if (pSymbol != NULL && pSession != NULL)  
    {  
        DWORD symbolTypeId;  
        pSymbol->get_typeId(&symbolTypeId);  
        pSession->symbolById(symbolTypeId, &pTypeSymbol);  
    }  
    return(pTypeSymbol);  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)