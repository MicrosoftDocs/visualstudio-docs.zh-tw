---
title: SetThreadCount | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- SetThreadCount
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a22e9819435114186e7b2d9afec02736f686537d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49280731"
---
# <a name="setthreadcount"></a>SetThreadCount
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
設定全域執行緒計數，並將該計數指派給目前的執行緒。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT WINAPI SetThreadCount(int threadCount);  
```  
  
#### <a name="parameters"></a>參數  
 [in] `threadCount`  
 要使用的執行緒數目。  
  
## <a name="return-value"></a>傳回值  
 [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) 與 [成功] (<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) 位元集，如果更新執行緒計數。  
  
## <a name="requirements"></a>需求  
 **標頭：** FileTracker.h



