---
title: PROFILER_HEAP_OBJECT_RELATIONSHIP 結構 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3ab3d986-3314-4c7b-a1c8-18ed691a8b9c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7a905a44f2ef686181c5a859699277d16f6cd374
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823617"
---
# <a name="profilerheapobjectrelationship-structure"></a>PROFILER_HEAP_OBJECT_RELATIONSHIP 結構
代表堆積物件的關聯性。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP{    PROFILER_HEAP_OBJECT_NAME_ID relationshipId;    PROFILER_RELATIONSHIP_INFO relationshipInfo;    [switch_type(PROFILER_RELATIONSHIP_INFO), switch_is(relationshipInfo)] union    {        [case(PROFILER_PROPERTY_TYPE_NUMBER)] double numberValue;        [case(PROFILER_PROPERTY_TYPE_STRING)] LPCWSTR stringValue;        [case(PROFILER_PROPERTY_TYPE_HEAP_OBJECT)] PROFILER_HEAP_OBJECT_ID objectId;        [case(PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT)] PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;    };} PROFILER_HEAP_OBJECT_RELATIONSHIP;  
```  
  
## <a name="members"></a>成員  
  
|成員|值|描述|  
|------------|-----------|-----------------|  
|relationshipId|[PROFILER_HEAP_OBJECT_NAME_ID 類型](../../winscript/reference/profiler-heap-object-name-id-type.md)|關聯性的識別碼名稱，從[IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)。|  
|relationshipInfo|[PROFILER_RELATIONSHIP_INFO 列舉](../../winscript/reference/profiler-relationship-info-enumeration.md)|關聯性的相關資訊。|  
|numberValue|double|數字的值。 只有其中一個`numberValue` / `stringValue` / `objectId` / `externalObjectAddress`設定，根據`relationshipInfo`值。|  
|stringValue|LPCWSTR|字串值。|  
|objectId|[PROFILER_HEAP_OBJECT_ID 類型](../../winscript/reference/profiler-heap-object-id-type.md)|堆積物件的識別碼。|  
|externalObjectAddress|[PROFILER_EXTERNAL_OBJECT_ADDRESS 類型](../../winscript/reference/profiler-external-object-address-type.md)|外部物件位址。|  
|subString|[PROFILER_PROPERTY_TYPE_SUBSTRING_INFO 結構](../../winscript/reference/profiler-property-type-substring-info-structure.md)|子字串類型的相關資訊。|