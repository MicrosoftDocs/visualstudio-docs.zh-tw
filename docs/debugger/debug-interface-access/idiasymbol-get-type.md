---
title: "Idiasymbol:: Get_type |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_type method
ms.assetid: 1c6a4176-dd4e-4c22-8b8f-0e559fc078ba
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67548053c45d48fa240fa836f5e59fa43edd1453
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgettype"></a>IDiaSymbol::get_type
擷取表示這個符號的類型的符號。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_type (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，代表這個符號的類型。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不適用於符號。  
  
## <a name="remarks"></a>備註  
 若要判斷有符號的類型，您必須呼叫這個方法，並檢查產生[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。 請注意，可能不具有類型的符號。 例如，結構的名稱有沒有類型，但是它可能會有子系符號 (使用[idiasymbol:: Findchildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)方法來檢查這些子系)。  
  
## <a name="example"></a>範例  
  
```C++  
IDiaSymbol*         pType;  
CComPtr<IDiaSymbol> pBaseType;  
if (SUCCEEDED(pType->get_type( &pBaseType ))) {  
    BasicType btBaseType;  
    if (SUCCEEDED(pBaseType->get_baseType((DWORD *)&btBaseType))) {  
        // Do something with basic type.  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Idiasymbol:: Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)