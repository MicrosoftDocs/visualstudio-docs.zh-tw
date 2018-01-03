---
title: WriteContextTLogs | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname: WriteContextTLogs
apilocation: filetracker.dll
apitype: COM
helpviewer_keywords: WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fb58b8e577893549e717a824b5c89d36fee2a65c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="writecontexttlogs"></a>WriteContextTLogs
寫入目前內容的記錄檔。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `intermediateDirectory`  
 儲存追蹤記錄的目錄。  
  
 [in] `tlogRootName`  
 記錄檔名稱的根名稱。  
  
## <a name="return-value"></a>傳回值  
 如已建立追蹤內容，則為 **HRESULT** 和已設定的 **SUCCEEDED** 位元。  
  
## <a name="requirements"></a>需求  
 **標頭：**FileTracker.h  
  
## <a name="see-also"></a>請參閱  
 [WriteAllTLogs](../msbuild/writealltlogs.md)