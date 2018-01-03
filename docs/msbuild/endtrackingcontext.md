---
title: EndTrackingContext | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname: EndTrackingContext
apilocation: filetracker.dll
apitype: COM
helpviewer_keywords: EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
caps.latest.revision: "3"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 976b6af01b26d6fb8738d1d418b09fb04a61c5c6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="endtrackingcontext"></a>EndTrackingContext
結束目前追蹤內容。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT WINAPI EndTrackingContext();  
```  
  
## <a name="return-value"></a>傳回值  
 如果已結束追蹤內容，則為已設定 **SUCCEEDED** 位元的 **HRESULT**。  
  
## <a name="requirements"></a>需求  
 **標頭：**FileTracker.h  
  
## <a name="see-also"></a>請參閱  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)