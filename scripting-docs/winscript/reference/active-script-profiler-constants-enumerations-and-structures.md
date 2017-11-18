---
title: "使用中指令碼分析工具的常數、 列舉和結構 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a37f64b14d0d732e48de66bb5268d47c95426937
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>動態指令碼分析工具的常數、列舉和結構
下列的列舉型別會使用使用中指令碼分析工具的介面。  
  
## <a name="constants-enumerations-and-structures"></a>常數、列舉和結構  
  
|常數|說明|  
|---------------|-----------------|  
|[PROFILER_EXTERNAL_OBJECT_ADDRESS 類型](../../winscript/reference/profiler-external-object-address-type.md)|分析工具外部物件位址。 用於[PROFILER_HEAP_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md)和[PROFILER_HEAP_OBJECT_RELATIONSHIP 結構](../../winscript/reference/profiler-heap-object-relationship-structure.md)。|  
|[PROFILER_HEAP_OBJECT_ID 類型](../../winscript/reference/profiler-heap-object-id-type.md)|堆積物件的識別碼。 用於[PROFILER_HEAP_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md)[PROFILER_HEAP_OBJECT_SCOPE_LIST 結構](../../winscript/reference/profiler-heap-object-scope-list-structure.md)， [PROFILER_HEAP_OBJECT_OPTIONAL_INFO 結構](../../winscript/reference/profiler-heap-object-optional-info-structure.md)，和[PROFILER_HEAP_OBJECT_RELATIONSHIP 結構](../../winscript/reference/profiler-heap-object-relationship-structure.md)。|  
|[PROFILER_HEAP_OBJECT_NAME_ID 類型](../../winscript/reference/profiler-heap-object-name-id-type.md)|堆積物件名稱的識別碼。 用於[PROFILER_HEAP_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md)。|  
  
|列舉|說明|  
|------------------|-----------------|  
|[PROFILER_EVENT_MASK 列舉](../../winscript/reference/profiler-event-mask-enumeration.md)|指出應該要分析的事件類型。|  
|[PROFILER_HEAP_ENUM_FLAGS 列舉](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|旗標，表示是否公開堆積物件指向物件關聯性中的相關額外資訊。 用於[iactivescriptprofilercontrol5:: Enumheap2 方法](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)。|  
|[PROFILER_HEAP_OBJECT_FLAGS 列舉](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|代表堆積物件的相關基本資訊的旗標。 用於[PROFILER_HEAP_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md)。|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE 列舉](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|代表不同類型的選擇性資訊。 用於[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 結構](../../winscript/reference/profiler-heap-object-optional-info-structure.md)。|  
|[PROFILER_RELATIONSHIP_INFO 列舉](../../winscript/reference/profiler-relationship-info-enumeration.md)|表示關聯性中物件的相關資訊。 用於[PROFILER_HEAP_OBJECT_RELATIONSHIP 結構](../../winscript/reference/profiler-heap-object-relationship-structure.md)。|  
|[PROFILER_SCRIPT_TYPE 列舉](../../winscript/reference/profiler-script-type-enumeration.md)|指定指令碼的類型。|  
  
|結構|說明|  
|----------------|-----------------|  
|[PROFILER_HEAP_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md)|代表堆積物件收集[iactivescriptprofilercontrol3:: Enumheap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)。|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 結構](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|代表堆積物件的選擇性資訊。|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP 結構](../../winscript/reference/profiler-heap-object-relationship-structure.md)|代表堆積物件的關聯性。|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 結構](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|表示屬於堆積物件的關聯性清單。|  
|[PROFILER_HEAP_OBJECT_SCOPE_LIST 結構](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|這個結構是僅限函式物件與相關聯。 範圍清單的範圍，其中每個範圍是堆積物件與相關聯的屬性清單，表示每個指定的範圍中的變數清單以表示函式的結束。 在某些情況下，在該範圍中的物件名稱可能無法使用，它們的 id。|  
|[PROFILER_PROPERTY_TYPE_SUBSTRING_INFO 結構](../../winscript/reference/profiler-property-type-substring-info-structure.md)|表示子字串類型的相關資訊。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼分析工具介面](../../winscript/reference/active-script-profiler-interfaces.md)