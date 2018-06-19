---
title: PROFILER_HEAP_OBJECT_SCOPE_LIST 結構 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67f0972faee11e15bd5d0e9a219e439df49d9672
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734258"
---
# <a name="profilerheapobjectscopelist-structure"></a>PROFILER_HEAP_OBJECT_SCOPE_LIST 結構
這個結構是僅限函式物件與相關聯。 範圍清單的範圍，其中每個範圍是堆積物件與相關聯的屬性清單，表示每個指定的範圍中的變數清單以表示函式的結束。 在某些情況下，範圍可能無法使用，在物件和其索引的屬性清單的名稱使用。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST{    UINT count;    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
```  
  
## <a name="members"></a>成員  
  
|成員|類型|描述|  
|------------|----------|-----------------|  
|count|UINT|範圍數目|  
|scopes|[PROFILER_HEAP_OBJECT_ID 類型](../../winscript/reference/profiler-heap-object-id-type.md)|陣列的範圍。|