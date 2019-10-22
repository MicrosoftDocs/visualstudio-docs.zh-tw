---
title: 動態指令碼分析工具的常數、列舉和結構 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a9409799c7da2ed3f4864dea0e7785635492220
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572686"
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>動態指令碼分析工具的常數、列舉和結構
動態指令碼分析工具介面會使用下列列舉。  
  
## <a name="constants-enumerations-and-structures"></a>常數、列舉和結構  
  
|常數|描述|  
|---------------|-----------------|  
|[PROFILER_EXTERNAL_OBJECT_ADDRESS 類型](../../winscript/reference/profiler-external-object-address-type.md)|分析工具的外部物件位址。 用於[PROFILER_HEAP_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md)和[PROFILER_HEAP_OBJECT_RELATIONSHIP 結構](../../winscript/reference/profiler-heap-object-relationship-structure.md)中。|  
|[PROFILER_HEAP_OBJECT_ID 類型](../../winscript/reference/profiler-heap-object-id-type.md)|堆積物件的識別碼。 用於[PROFILER_HEAP_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md)[PROFILER_HEAP_OBJECT_SCOPE_LIST 結構](../../winscript/reference/profiler-heap-object-scope-list-structure.md)、 [PROFILER_HEAP_OBJECT_OPTIONAL_INFO 結構](../../winscript/reference/profiler-heap-object-optional-info-structure.md)和[PROFILER_HEAP_OBJECT_RELATIONSHIP 結構](../../winscript/reference/profiler-heap-object-relationship-structure.md)。|  
|[PROFILER_HEAP_OBJECT_NAME_ID 類型](../../winscript/reference/profiler-heap-object-name-id-type.md)|堆積物件的名稱識別碼。 用於[PROFILER_HEAP_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md)中。|  
  
|列舉|描述|  
|------------------|-----------------|  
|[PROFILER_EVENT_MASK 列舉](../../winscript/reference/profiler-event-mask-enumeration.md)|表示應該分析的事件種類。|  
|[PROFILER_HEAP_ENUM_FLAGS 列舉](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|表示是否公開物件關聯性中所指向之堆積物件的額外資訊的旗標。 用於[IActiveScriptProfilerControl5：： EnumHeap2 方法](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)中。|  
|[PROFILER_HEAP_OBJECT_FLAGS 列舉](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|表示堆積物件之基本資訊的旗標。 用於[PROFILER_HEAP_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md)中。|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE 列舉](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|代表不同類型的選擇性資訊。 用於[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 結構](../../winscript/reference/profiler-heap-object-optional-info-structure.md)中。|  
|[PROFILER_RELATIONSHIP_INFO 列舉](../../winscript/reference/profiler-relationship-info-enumeration.md)|表示關聯性中物件的相關資訊。 用於[PROFILER_HEAP_OBJECT_RELATIONSHIP 結構](../../winscript/reference/profiler-heap-object-relationship-structure.md)中。|  
|[PROFILER_SCRIPT_TYPE 列舉](../../winscript/reference/profiler-script-type-enumeration.md)|指定腳本的類型。|  
  
|結構|描述|  
|----------------|-----------------|  
|[PROFILER_HEAP_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md)|表示[IActiveScriptProfilerControl3：： EnumHeap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)所收集的堆積物件。|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 結構](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|表示有關堆積物件的選擇性資訊。|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP 結構](../../winscript/reference/profiler-heap-object-relationship-structure.md)|表示堆積物件的關聯性。|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 結構](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|表示屬於堆積物件之關聯性的清單。|  
|[PROFILER_HEAP_OBJECT_SCOPE_LIST 結構](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|這個結構僅與函數物件相關聯。 範圍清單會將函式的關閉表示為範圍清單，其中每個範圍都是具有相關聯屬性清單的堆積物件，代表每個指定範圍中的變數。 在某些情況下，該範圍內的物件名稱可能無法使用，只有其識別碼。|  
|[PROFILER_PROPERTY_TYPE_SUBSTRING_INFO 結構](../../winscript/reference/profiler-property-type-substring-info-structure.md)|表示子字串類型的相關資訊。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼分析工具介面](../../winscript/reference/active-script-profiler-interfaces.md)