---
title: "PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 結構 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 46ca87ea-5b0f-437d-a33f-b2d9a457e036
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fdad752587869fbdd1edfa325ddc1282cfa3a95
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="profilerheapobjectrelationshiplist-structure"></a>PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 結構
表示屬於堆積物件的關聯性清單。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST{    UINT count;    [size_is(count)] PROFILER_HEAP_OBJECT_RELATIONSHIP elements[];} PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST;  
```  
  
## <a name="members"></a>成員  
  
|成員|類型|描述|  
|------------|----------|-----------------|  
|count|UINT|堆積物件的關聯性數目。|  
|項目|[PROFILER_HEAP_OBJECT_RELATIONSHIP 結構](../../winscript/reference/profiler-heap-object-relationship-structure.md)|堆積物件的關聯性。|