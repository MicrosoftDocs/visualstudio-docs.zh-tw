---
title: 'Idiasymbol:: Get_value |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaSymbol::get_value method
ms.assetid: 2e40174a-2a61-4e5f-bb32-9e0ceec2178a
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 278e199400fa46782035ec767e65f72040d47c4a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49870220"
---
# <a name="idiasymbolgetvalue"></a>IDiaSymbol::get_value
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取常數的值。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_value (   
   VARIANT* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [in、 out]A`VARIANT`常數的值會填入的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。  
  
## <a name="remarks"></a>備註  
 傳遞至這個方法之前，必須先初始化所提供的變數。 如需詳細資訊，請參閱範例。  
  
## <a name="example"></a>範例  
  
```cpp#  
void ProcessValue(IDiaSymbol *pSymbol)  
{  
    VARIANT value;  
    value.vt = VT_EMPTY;    // Initialize variant for use.  
    if (pSymbol->get_value(&value) == S_OK)  
    {  
        // Do something with value.  
    }  
}  
  
//----------------------------------------------------  
// Alternate approach  
void ProcessValue2(IDiaSymbol *pSymbol)  
{  
    CComVariant value;  
    if (pSymbol->get_value(&value) == S_OK)  
    {  
        // Do something with value  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



