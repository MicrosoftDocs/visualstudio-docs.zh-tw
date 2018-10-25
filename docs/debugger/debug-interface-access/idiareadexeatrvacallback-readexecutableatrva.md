---
title: 'Idiareadexeatrvacallback:: Readexecutableatrva |Microsoft Docs'
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
ms.openlocfilehash: 69afacf68c77dcb2bca7c951dbd2a1ee9a344cfb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917274"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
讀取指定起始於指定相對虛擬位址 (RVA) 從可執行檔的位元組數目。  
  
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
 [in、 out]陣列，其中會填入從檔案讀取的位元組。  
  
## <a name="remarks"></a>備註  
 DIA 支援程式碼，從可執行檔使用的相對虛擬位址載入資料的位元組被呼叫此方法。 會呼叫這個方法支援[idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)