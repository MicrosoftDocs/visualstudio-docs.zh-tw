---
title: "Idiareadexeatoffsetcallback:: Readexecutableat |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8cb9ff60968d806cfdee0201746a02483895b0af
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
讀取指定的從可執行檔的指定位移處開始的位元組數目。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 fileOffset  
 [in]若要開始讀取的可執行檔中的位移。  
  
 cbData  
 [in]要讀取的位元組數目。  
  
 pcbData  
 [out]傳回讀取的位元組數目。  
  
 [資料]  
 [in、 out]陣列，其中已填入從檔案讀取的位元組。  
  
## <a name="remarks"></a>備註  
 從使用絕對檔案位移的可執行檔載入資料位元組的 DIA 支援程式碼會呼叫這個方法。 這個方法呼叫支援[idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)