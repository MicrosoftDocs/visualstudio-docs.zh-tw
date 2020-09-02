---
title: StartTrackingContext | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- StartTrackingContext
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- StartTrackingContext
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da002fe757d623a665b39c16cc10e77e492e2660
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199939"
---
# <a name="starttrackingcontext"></a>StartTrackingContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

啟動追蹤內容。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);  
```  
  
#### <a name="parameters"></a>參數  
 [in] `intermediateDirectory`  
 儲存追蹤記錄的目錄。  
  
 [in] `taskName`  
 找到追蹤內容。 這個名稱是用來建立記錄檔的名稱。  
  
## <a name="return-value"></a>傳回值  
 [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->具有 [SUCCEEDED] ( 的 ) <!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->如果已建立追蹤內容，則為 ) 位集。  
  
## <a name="requirements"></a>需求  
 **標頭：** FileTracker.h
