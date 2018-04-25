---
title: 'Idiaenumsectioncontribs:: Next |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 6f700ef7160cff643c2a60007d7b1f83ecbe4eeb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumsectioncontribsnext"></a>IDiaEnumSectionContribs::Next
擷取指定的數目的列舉順序中的區段比重。  
  
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
 [in]要擷取列舉值中的區段比重數目。  
  
 rgelt  
 [out]要填入的陣列[IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)代表所需的區段比重的物件。  
  
 pceltFetched  
 [out]擷取列舉值中傳回區段比重的數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`。 傳回`S_FALSE`如果沒有更多的區段比重。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)