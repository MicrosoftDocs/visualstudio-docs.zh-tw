---
title: "Idialoadcallback:: Notifydebugdir |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3bc5150146953dc99970da82747c6e608660b104
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
.Exe 檔案中找不到偵錯目錄時呼叫。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `fExecutable`  
 [in]`TRUE`如果偵錯目錄唯讀的可執行檔 （而非.dbg 檔案）。  
  
 `cbData`  
 [in]偵錯目錄中的資料位元組的計數。  
  
 `data[]`  
 [in]陣列，其中會填入偵錯目錄。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 傳回碼通常會被忽略。  
  
## <a name="remarks"></a>備註  
 [Idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法在處理的可執行檔時發現偵錯目錄時，會叫用此回呼。  
  
 這個方法會移除用戶端進行反向工程，可執行檔和/或偵錯檔案需要支援以外的.pdb 檔中找到的偵錯資訊。 使用此資料，用戶端可以識別可用的偵錯資訊的類型，以及是否位於可執行檔或.dbg 檔案中。  
  
 大部分的用戶端將不需要此回呼，因為`IDiaDataSource::loadDataForExe`方法明確地開啟.pdb 和.dbg 檔案時所需做的符號。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)