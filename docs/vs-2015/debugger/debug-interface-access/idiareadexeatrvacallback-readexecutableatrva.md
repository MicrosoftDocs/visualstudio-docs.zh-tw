---
title: 'Idiareadexeatrvacallback:: Readexecutableatrva |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a94993260c7614b56d5b357c26793be7d1775e37
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750300"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

讀取指定起始於指定相對虛擬位址 (RVA) 從可執行檔的位元組數目。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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



