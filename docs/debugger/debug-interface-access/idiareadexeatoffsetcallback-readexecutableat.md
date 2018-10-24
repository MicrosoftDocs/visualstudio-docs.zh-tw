---
title: 'Idiareadexeatoffsetcallback:: Readexecutableat |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a9f1c1ab49205a299b73837685b3d35b352a855d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837980"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
讀取指定的可執行檔從指定的位移開始的位元組數目。  
  
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
 [in、 out]陣列，其中會填入從檔案讀取的位元組。  
  
## <a name="remarks"></a>備註  
 DIA 支援程式碼，從使用絕對檔案位移的可執行檔載入資料的位元組被呼叫此方法。 會呼叫這個方法支援[idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)