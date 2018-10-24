---
title: 'Idiaenumsourcefiles:: Next |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Next method
ms.assetid: 83bf6317-ff39-4c5c-8987-cba34e7a6983
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fef2d096ca522a6f6f2a05a081fb5a5a494e168c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819924"
---
# <a name="idiaenumsourcefilesnext"></a>IDiaEnumSourceFiles::Next
擷取列舉序列中的原始程式檔中指定的數目。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT Next (   
   ULONG            celt,  
   IDiaSourceFile** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 celt  
 [in]要擷取列舉值中的來源檔案的數目。  
  
 rgelt  
 [out]陣列，其中是要在以填滿[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)代表所需的原始程式檔的物件。  
  
 pceltFetched  
 [out]擷取列舉值中傳回原始程式檔的數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`。 傳回`S_FALSE`如果不有任何更多的原始程式檔。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [Idiasession:: Findlinesbylinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)