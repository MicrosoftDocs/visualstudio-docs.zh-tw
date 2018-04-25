---
title: 'Idiaenumsymbols:: Skip |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Skip method
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 65e96f2f03229b12c378a096ecfd7555af1f5cce
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumsymbolsskip"></a>IDiaEnumSymbols::Skip
略過指定的數目的列舉順序中的符號。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>參數  
 celt  
 [in]略過將列舉序列中的符號數。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`是否有任何符號略過。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)