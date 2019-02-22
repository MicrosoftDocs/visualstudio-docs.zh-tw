---
title: IDiaSymbol::get_typeIds | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d06648c884a4406c6a5d28b2b33a7cbfd4f6d24
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54987462"
---
# <a name="idiasymbolgettypeids"></a>IDiaSymbol::get_typeIds
擷取這個符號的編譯器特定的型別識別項值的陣列。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_typeIds (   
   DWORD  cTypeIds,  
   DWORD* pcTypeIds,  
   DWORD  typeIds[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cTypeIds`  
 [in]保留的資料緩衝區的大小。  
  
 `pcTypeIds`  
 [out]傳回的數目`typeIds`撰寫，或者，如果`typeIds`是`NULL`，然後可以使用的型別識別項的總數。  
  
 `typeIds[]`  
 [out]陣列，其中是要被填入型別識別項。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)