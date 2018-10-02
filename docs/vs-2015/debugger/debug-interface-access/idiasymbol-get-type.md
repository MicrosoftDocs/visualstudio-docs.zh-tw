---
title: 'Idiasymbol:: Get_type |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_type method
ms.assetid: 1c6a4176-dd4e-4c22-8b8f-0e559fc078ba
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 240be23528bc648fe3bfe2f4715aae96fcbcd6d2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498020"
---
# <a name="idiasymbolgettype"></a>IDiaSymbol::get_type
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[idiasymbol:: Get_type](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-type)。  
  
擷取代表這個符號的類型的符號。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_type (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，表示這個符號的類型。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。  
  
## <a name="remarks"></a>備註  
 若要判斷有符號的類型，您必須呼叫這個方法，並檢查產生[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。 請注意，可能不具有類型的符號。 例如，結構的名稱有任何類型，但是它可能會有子系符號 (使用[idiasymbol:: Findchildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)方法來檢查這些子系)。  
  
## <a name="example"></a>範例  
  
```cpp#  
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



