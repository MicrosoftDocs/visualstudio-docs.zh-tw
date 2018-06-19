---
title: 'Idiaenumsymbols:: Next |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Next method
ms.assetid: bfe5fe27-6a84-4392-910f-e325146d7552
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f419716901d35ea667f5e99a0c452d6e1b4d186c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459619"
---
# <a name="idiaenumsymbolsnext"></a>IDiaEnumSymbols::Next
擷取指定的數目的列舉順序中的符號。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT Next (   
   ULONG        celt,  
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 celt  
 [in]要擷取列舉值中的符號數目。  
  
 rgelt  
 [out]陣列，其中是要在以填滿[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，代表所要的符號。  
  
 pceltFetched  
 [out]擷取列舉值中傳回符號的數。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`。 傳回`S_FALSE`是否有任何符號。 反之則傳回錯誤碼。  
  
## <a name="example"></a>範例  
  
```C++  
IDiaEnumSymbols* pEnum  
CComPtr< IDiaSymbol> pSym;  
DWORD celt;  
pEnum->Next( 1, &pSym, &celt );  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [Idiasession:: Findlinesbylinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)