---
title: IDiaSymbol::get_type | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_type method
ms.assetid: 1c6a4176-dd4e-4c22-8b8f-0e559fc078ba
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9bec7cdbf0641bbd1bba1e70c2f21ec232a18e6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838831"
---
# <a name="idiasymbolget_type"></a>IDiaSymbol::get_type
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取表示此符號之類型的符號。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_type (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展傳回代表此符號類型的 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。  
  
## <a name="remarks"></a>備註  
 若要判斷符號具有的型別，您必須呼叫這個方法，並檢查產生的 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件。 請注意，符號可能沒有類型。 例如，結構名稱沒有類型，但可能有子符號 (使用 [IDiaSymbol：： findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md) 方法來檢查這些子系) 。  
  
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
 [IDiaSymbol：： get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
