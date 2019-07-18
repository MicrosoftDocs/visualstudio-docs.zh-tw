---
title: 'Idiaenumlinenumbers:: Next |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Next method
ms.assetid: 363d5b40-1316-4ab8-836f-63637f619e0a
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ebf4016b3bff52a74607fe01918655c0587f51d9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68190097"
---
# <a name="idiaenumlinenumbersnext"></a>IDiaEnumLineNumbers::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取指定的數目的列舉型別序列中的行號。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Next (   
   ULONG            celt,  
   IDiaLineNumber** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 celt  
 [in]要擷取列舉值中的行號的數字。  
  
 rgelt  
 [out]傳回的陣列[IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)物件，代表所要的行號。  
  
 pceltFetched  
 [out]擷取列舉值中傳回列數字的數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`有沒有更多的行號。 否則會傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
