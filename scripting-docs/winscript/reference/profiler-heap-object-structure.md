---
title: "PROFILER_HEAP_OBJECT 結構 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9f35362c-6856-4cfb-b990-031a156a58eb
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad50f03806cbf98450c0fc917f1a97ca7305d05c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="profilerheapobject-structure"></a>PROFILER_HEAP_OBJECT 結構
代表堆積物件收集[iactivescriptprofilercontrol3:: Enumheap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct _PROFILER_HEAP_OBJECT  
{  
    UINT size;    union {        PROFILER_HEAP_OBJECT_ID objectId;        PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;    };    PROFILER_HEAP_OBJECT_NAME_ID typeNameId;    USHORT flags;     USHORT optionalInfoCount;} PROFILER_HEAP_OBJECT;  
```  
  
## <a name="members"></a>成員  
  
|成員|類型|描述|  
|------------|----------|-----------------|  
|objectId|[PROFILER_HEAP_OBJECT_ID 類型](../../winscript/reference/profiler-heap-object-id-type.md)|堆積物件的識別碼。|  
|externalObjectAddress|[PROFILER_EXTERNAL_OBJECT_ADDRESS 類型](../../winscript/reference/profiler-external-object-address-type.md)|物件，例如 c + + 配置的物件，超出 JavaScript 堆積的外部物件位址。|  
|typeNameId|[PROFILER_HEAP_OBJECT_NAME_ID 類型](../../winscript/reference/profiler-heap-object-name-id-type.md)|從堆積物件型別名稱的識別碼擷取[IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)。 只有其中一個`externalObjectAddress`或`typeName`取決於存在於`flags`值。|  
|旗標|[PROFILER_HEAP_OBJECT_FLAGS 列舉](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|包含堆積物件的相關基本資訊的旗標。|  
|optionalInfoCount|USHORT|數目[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 結構](../../winscript/reference/profiler-heap-object-optional-info-structure.md)記錄可供使用的堆積物件。|