---
title: PROFILER_HEAP_OBJECT 結構 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 9f35362c-6856-4cfb-b990-031a156a58eb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1652c6ebffff88782ffcc879158a5142f22395d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823810"
---
# <a name="profilerheapobject-structure"></a>PROFILER_HEAP_OBJECT 結構
代表堆積物件來收集[IActiveScriptProfilerControl3::EnumHeap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT  
{  
    UINT size;    union {        PROFILER_HEAP_OBJECT_ID objectId;        PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;    };    PROFILER_HEAP_OBJECT_NAME_ID typeNameId;    USHORT flags;     USHORT optionalInfoCount;} PROFILER_HEAP_OBJECT;  
```  
  
## <a name="members"></a>成員  
  
|成員|類型|描述|  
|------------|----------|-----------------|  
|objectId|[PROFILER_HEAP_OBJECT_ID 類型](../../winscript/reference/profiler-heap-object-id-type.md)|堆積物件的識別碼。|  
|externalObjectAddress|[PROFILER_EXTERNAL_OBJECT_ADDRESS 類型](../../winscript/reference/profiler-external-object-address-type.md)|外部物件位址的物件，例如C++-配置超出 JavaScript 堆積的物件。|  
|typeNameId|[PROFILER_HEAP_OBJECT_NAME_ID 類型](../../winscript/reference/profiler-heap-object-name-id-type.md)|從擷取的堆積物件型別名稱識別碼[IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)。 只有其中一個`externalObjectAddress`或是`typeName`取決於存在`flags`值。|  
|旗標|[PROFILER_HEAP_OBJECT_FLAGS 列舉](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|包含堆積物件的基本資訊的旗標。|  
|optionalInfoCount|USHORT|數目[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 結構](../../winscript/reference/profiler-heap-object-optional-info-structure.md)記錄可供使用的堆積物件。|