---
title: 'Idiasymbol:: Get_typeids |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f1ad4aae54096ea2fdcbcac1a68d32fc3b386ad
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgettypeids"></a>IDiaSymbol::get_typeIds
擷取這個符號的編譯器專用的類型識別碼值的陣列。  
  
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
 [out]傳回的數目`typeIds`所撰寫，或者，如果`typeIds`是`NULL`，然後類型識別項的總數。  
  
 `typeIds[]`  
 [out]陣列，其中是要被填入類型識別項。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不適用於符號。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)