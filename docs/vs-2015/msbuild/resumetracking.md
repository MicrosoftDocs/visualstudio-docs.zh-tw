---
title: ResumeTracking | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- ResumeTracking
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 75c1a94e9db6e1a141668f6ba314c39cedc3fd6c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159225"
---
# <a name="resumetracking"></a>ResumeTracking
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在目前的內容中繼續追蹤。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT WINAPI ResumeTracking();  
```  
  
## <a name="return-value"></a>傳回值  
 [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) 以 [成功] （<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) 位元集，如果追蹤已繼續。 [E_FAIL](<!-- TODO: review code entity reference <xref:assetId:///E_FAIL?qualifyHint=False&amp;autoUpgrade=True>  -->) 會傳回因為內容無法使用，如果無法繼續追蹤。  
  
## <a name="requirements"></a>需求  
 **標頭：** FileTracker.h  
  
## <a name="see-also"></a>另請參閱  
 [SuspendTracking](../msbuild/suspendtracking.md)
