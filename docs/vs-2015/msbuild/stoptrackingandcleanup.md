---
title: StopTrackingAndCleanup | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- StopTrackingAndCleanup
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4cb07a98728612ae5c0930b23e4f76a5672284aa
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54835104"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
停止所有的追蹤，並釋放追蹤工作階段使用的所有記憶體。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## <a name="return-value"></a>傳回值  
 如已停止追蹤，則傳回已設定 [SUCCEEDED](<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) 位元的 [HRESULT](<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->)。  
  
## <a name="requirements"></a>需求  
 **標頭：** FileTracker.h  
  
## <a name="see-also"></a>請參閱  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)
