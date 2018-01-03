---
title: ResumeTracking | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname: ResumeTracking
apilocation: filetracker.dll
apitype: COM
helpviewer_keywords: ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ae79812a700f8444002ae3b8c04c0ea816970eea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="resumetracking"></a>ResumeTracking
在目前的內容中繼續追蹤。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT WINAPI ResumeTracking();  
```  
  
## <a name="return-value"></a>傳回值  
 如已繼續追蹤，則為 **HRESULT** 和已設定的 **SUCCEEDED** 位元。 如果因為無法取得內容而無法繼續追蹤，則傳回 **E_FAIL**。  
  
## <a name="requirements"></a>需求  
 **標頭：**FileTracker.h  
  
## <a name="see-also"></a>請參閱  
 [SuspendTracking](../msbuild/suspendtracking.md)