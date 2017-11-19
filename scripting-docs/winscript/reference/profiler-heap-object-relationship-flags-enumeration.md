---
title: "PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS 列舉 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab542225e0238dbd40f90d9de66d43d0791e05e0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="profilerheapobjectrelationshipflags-enumeration"></a>PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS 列舉
代表是否堆積物件指向的物件關聯性中的旗標是 getter 或 setter 方法。 用於[EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)方法中指定 PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS 值時`enumFlags`參數。  
  
## <a name="syntax"></a>語法  
  
```  
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
```  
  
## <a name="members"></a>成員  
  
|成員|值|描述|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE|0x00000000|此物件關聯性中所指向的堆積物件不會被視為 getter 或 setter 方法。|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR|0x00010000|指向物件關聯性中的堆積物件是 getter 方法。 這項資訊會儲存在高的 2 個位元組 （16 位元） 的[PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md)欄位。|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR|0x00020000|指向物件關聯性中的堆積物件是 setter 方法。 這項資訊會儲存在高的 2 個位元組 （16 位元） 的`PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo`欄位。|