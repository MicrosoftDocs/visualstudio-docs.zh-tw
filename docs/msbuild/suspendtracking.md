---
title: SuspendTracking | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname: SuspendTracking
apilocation: filetracker.dll
apitype: COM
helpviewer_keywords: SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
caps.latest.revision: "3"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: c00b78b3a1d69b0d68abf9d07615bc1875ffc5a4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="suspendtracking"></a>SuspendTracking
在目前的內容中暫停追蹤。  
  
## <a name="syntax"></a>語法  
  
```cpp 
HRESULT WINAPI SuspendTracking(void);  
```  
  
## <a name="return-value"></a>傳回值  
 如已暫停追蹤，則為 **HRESULT** 和已設定的 **SUCCEEDED** 位元。  
  
## <a name="requirements"></a>需求  
 **標頭：**FileTracker.h  
  
## <a name="see-also"></a>另請參閱  
 [ResumeTracking](../msbuild/resumetracking.md)