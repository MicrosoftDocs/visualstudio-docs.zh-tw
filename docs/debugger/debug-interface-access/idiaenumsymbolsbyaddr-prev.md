---
title: 'Idiaenumsymbolsbyaddr:: Prev |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Prev method
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e165268c1d31c61ba671f6087cc9922bf37e4103
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49870272"
---
# <a name="idiaenumsymbolsbyaddrprev"></a>IDiaEnumSymbolsByAddr::Prev
擷取位址中順序的上一個符號。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT Prev (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 celt  
 [in]要擷取列舉值中的符號數目。  
  
 rgelt  
 [out]陣列，其中是要在以填滿[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，代表所需的符號。  
  
 pceltFetched  
 [out]擷取列舉值中傳回符號的數。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`。 傳回`S_FALSE`如果不有任何先前的符號。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法會更新列舉值位置所擷取的項目數目。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)