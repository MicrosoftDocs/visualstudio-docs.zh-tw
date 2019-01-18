---
title: 動態指令碼 Profiler 常數、 列舉和結構 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d367374e4402da2d30cd8a855a509299363f882
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349123"
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>動態指令碼分析工具的常數、列舉和結構
使用中的指令碼 Profiler 介面會使用下列的列舉型別。  
  
## <a name="constants-enumerations-and-structures"></a>常數、列舉和結構  
  
|常數|描述|  
|---------------|-----------------|  
|[PROFILER_EXTERNAL_OBJECT_ADDRESS 類型](../../winscript/reference/profiler-external-object-address-type.md)|分析工具外部物件位址。 用於[PROFILER_HEAP_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md)並[PROFILER_HEAP_OBJECT_RELATIONSHIP 結構](../../winscript/reference/profiler-heap-object-relationship-structure.md)。|  
|[PROFILER_HEAP_OBJECT_ID 類型](../../winscript/reference/profiler-heap-object-id-type.md)|堆積物件的識別碼。 用於[PROFILER_HEAP_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md)[PROFILER_HEAP_OBJECT_SCOPE_LIST 結構](../../winscript/reference/profiler-heap-object-scope-list-structure.md)， [PROFILER_HEAP_OBJECT_OPTIONAL_INFO 結構](../../winscript/reference/profiler-heap-object-optional-info-structure.md)，以及[PROFILER_HEAP_OBJECT_RELATIONSHIP 結構](../../winscript/reference/profiler-heap-object-relationship-structure.md)。|  
|[PROFILER_HEAP_OBJECT_NAME_ID 類型](../../winscript/reference/profiler-heap-object-name-id-type.md)|堆積物件的名稱識別碼。 用於[PROFILER_HEAP_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md)。|  
  
|列舉|描述|  
|------------------|-----------------|  
|[PROFILER_EVENT_MASK 列舉](../../winscript/reference/profiler-event-mask-enumeration.md)|指出應該要分析的事件類型。|  
|[PROFILER_HEAP_ENUM_FLAGS 列舉](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|旗標，表示是否公開物件關聯性中指向的堆積物件的額外資訊。 用於[IActiveScriptProfilerControl5::EnumHeap2 方法](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)。|  
|[PROFILER_HEAP_OBJECT_FLAGS 列舉](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|代表堆積物件的基本資訊的旗標。 用於[PROFILER_HEAP_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md)。|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE 列舉](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|代表不同類型的選擇性資訊。 用於[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 結構](../../winscript/reference/profiler-heap-object-optional-info-structure.md)。|  
|[PROFILER_RELATIONSHIP_INFO 列舉](../../winscript/reference/profiler-relationship-info-enumeration.md)|表示關聯性中物件的相關資訊。 用於[PROFILER_HEAP_OBJECT_RELATIONSHIP 結構](../../winscript/reference/profiler-heap-object-relationship-structure.md)。|  
|[PROFILER_SCRIPT_TYPE 列舉](../../winscript/reference/profiler-script-type-enumeration.md)|指定指令碼的類型。|  
  
|結構|描述|  
|----------------|-----------------|  
|[PROFILER_HEAP_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md)|代表堆積物件來收集[IActiveScriptProfilerControl3::EnumHeap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)。|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 結構](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|代表堆積物件的選擇性資訊。|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP 結構](../../winscript/reference/profiler-heap-object-relationship-structure.md)|代表堆積物件的關聯性。|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 結構](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|表示屬於堆積物件的關聯性清單。|  
|[PROFILER_HEAP_OBJECT_SCOPE_LIST 結構](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|此結構是僅限函式物件相關聯。 範圍清單表示函式的 closure 的範圍，其中每個範圍是堆積物件與相關聯的屬性清單，表示每個指定的範圍內的變數清單。 在某些情況下，在該範圍中物件的名稱可能無法使用，它們的 id。|  
|[PROFILER_PROPERTY_TYPE_SUBSTRING_INFO 結構](../../winscript/reference/profiler-property-type-substring-info-structure.md)|表示子字串類型的相關資訊。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼分析工具介面](../../winscript/reference/active-script-profiler-interfaces.md)