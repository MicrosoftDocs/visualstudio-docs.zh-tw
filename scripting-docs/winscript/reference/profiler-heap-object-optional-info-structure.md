---
title: PROFILER_HEAP_OBJECT_OPTIONAL_INFO 結構 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 77e638bd-ae36-4292-a170-90a0c500e610
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c7f28499b5d6e1e01caab1e6fd83fc5ab72ccf6
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151033"
---
# <a name="profilerheapobjectoptionalinfo-structure"></a>PROFILER_HEAP_OBJECT_OPTIONAL_INFO 結構
代表堆積物件的選擇性資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT_OPTIONAL_INFO{    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE infoType;    [switch_type(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE), switch_is(infoType)] union    {        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE)] PROFILER_HEAP_OBJECT_ID prototype;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME)] LPCWSTR functionName;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE)] UINT elementAttributesSize;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE)] UINT elementTextChildrenSize;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST)] PROFILER_HEAP_OBJECT_SCOPE_LIST* scopeList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY)] PROFILER_HEAP_OBJECT_RELATIONSHIP* internalProperty;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* namePropertyList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* indexPropertyList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* relationshipList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* eventList;    };} PROFILER_HEAP_OBJECT_OPTIONAL_INFO;  
```  
  
## <a name="members"></a>成員  
  
|成員|類型|描述|  
|------------|----------|-----------------|  
|infoType|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE 列舉](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|選擇性的資訊類型。|  
|原型|[PROFILER_HEAP_OBJECT_ID 類型](../../winscript/reference/profiler-heap-object-id-type.md)|堆積物件的原型物件的識別碼。|  
|functionName|LPCWSTR|堆積物件的函式名稱。|  
|elementAttributesSize|UINT|堆積物件的項目屬性的大小。|  
|elementTextChildrenSize|UINT|堆積物件的文字子系的大小。|  
|scopeList|[PROFILER_HEAP_OBJECT_SCOPE_LIST 結構](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|堆積物件的範圍清單。|  
|internalProperty|[PROFILER_HEAP_OBJECT_RELATIONSHIP 結構](../../winscript/reference/profiler-heap-object-relationship-structure.md)|堆積物件的內部屬性。|  
|namePropertyList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 結構](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|堆積物件的名稱屬性的清單。|  
|indexPropertyList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 結構](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|堆積物件的索引屬性的清單。|  
|relationshipList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 結構](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|堆積物件的關聯性清單。|  
|eventList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 結構](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|堆積物件的事件清單。|