---
title: 'Idiaenumsectioncontribs:: Next |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Next method
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 915588402264ac6ba7076f3e9cd95b347b946689
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53936265"
---
# <a name="idiaenumsectioncontribsnext"></a>IDiaEnumSectionContribs::Next
擷取指定的數目的列舉型別序列中的區段比重。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT Next(   
   ULONG                celt,   
   IDiaSectionContrib** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 celt  
 [in]要擷取列舉值中的區段貢獻數目。  
  
 rgelt  
 [out]要填入的陣列[IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)代表所需的區段貢獻的物件。  
  
 pceltFetched  
 [out]擷取列舉值中傳回區段貢獻的數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`有沒有更多區段貢獻。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)