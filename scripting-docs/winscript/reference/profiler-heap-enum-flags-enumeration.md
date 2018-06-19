---
title: PROFILER_HEAP_ENUM_FLAGS 列舉 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 17936b7a-40d5-4774-b92b-b24ee391591e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2a7a27f4d9d7f834b07a2db5ba8433b63222a3b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734108"
---
# <a name="profilerheapenumflags-enumeration"></a>PROFILER_HEAP_ENUM_FLAGS 列舉
旗標，表示是否公開堆積物件指向物件關聯性中的相關額外資訊。 用於[EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
typedef [v1_enum] enum {    PROFILER_HEAP_ENUM_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS  = 0x00000001,} PROFILER_HEAP_ENUM_FLAGS;  
```  
  
## <a name="members"></a>成員  
  
|成員|值|描述|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_ENUM_FLAGS_NONE|0x00000000|此堆積物件未公開的物件關聯性的額外資訊。 此堆積物件的行為方式與[IActiveScriptProfilerControl3::HeapEnum](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)。|  
|PROFILER_HEAP_ENUM_ENUM_ STORE_RELATIONSHIP_FLAGS|0x00000001|此堆積物件會公開物件關聯性中所指向的物件是否不是 getter 或 setter 方法的相關資訊。 這項資訊會儲存在高的 2 個位元組 （16 位元） 的[PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md)欄位做為其中一個[PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS](../../winscript/reference/profiler-heap-object-relationship-flags-enumeration.md)列舉值。|  
|PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|0x00000002|此堆積物件用來正確顯示子字串。|  
|PROFILER_HEAP_ENUM_FLAGS_RELATIONSHIP_SUBSTRINGS|PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS &#124;PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|此堆積物件用來正確顯示子字串。|