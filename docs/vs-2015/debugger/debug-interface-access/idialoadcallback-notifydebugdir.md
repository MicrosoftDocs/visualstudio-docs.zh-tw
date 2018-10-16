---
title: 'Idialoadcallback:: Notifydebugdir |Microsoft Docs'
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
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ecb14b340df745ebb06d4bf7da571916e0ae6760
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262388"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

當偵錯已找到的目錄中的.exe 檔案時呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 [in]偵錯目錄中的資料位元組數目。  
  
 `data[]`  
 [in]陣列，其中會填入偵錯目錄。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。 傳回碼通常會被忽略。  
  
## <a name="remarks"></a>備註  
 [Idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法在處理的可執行檔時發現偵錯目錄時，會叫用這個回呼。  
  
 這個方法會移除用戶端進行反向工程的可執行檔和/或偵錯的檔案需要支援以外的.pdb 檔案中找到的偵錯資訊。 使用此資料，用戶端，可以識別可用的偵錯資訊的類型，以及是否位於可執行檔或.dbg 檔案。  
  
 大部分的用戶端將不需要此回撥，因為`IDiaDataSource::loadDataForExe`方法明確地開啟.pdb 和.dbg 檔案時需要符號。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)



