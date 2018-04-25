---
title: 'Idiareadexeatrvacallback:: Readexecutableatrva |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f71db30a3e4cba957e6aba0981587276af714e3e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
讀取指定的開始的指定相對虛擬位址 (RVA) 從可執行檔的位元組數目。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `relativeVirtualAddress`  
 [in]可執行檔中開始讀取的 RVA。  
  
 `cbData`  
 [in]要讀取的位元組數目。  
  
 `pcbData`  
 [out]傳回讀取的位元組數目。  
  
 `data[]`  
 [in、 out]陣列，其中已填入從檔案讀取的位元組。  
  
## <a name="remarks"></a>備註  
 從使用的相對虛擬位址的可執行檔載入資料位元組的 DIA 支援程式碼會呼叫這個方法。 這個方法呼叫支援[idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)