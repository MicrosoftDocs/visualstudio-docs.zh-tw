---
title: 'Iactivescriptprofilerheapenum:: Getoptionalinfo 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6ad237f2feb173408e895984dab7e7455004d16
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724678"
---
# <a name="iactivescriptprofilerheapenumgetoptionalinfo-method"></a>IActiveScriptProfilerHeapEnum::GetOptionalInfo 方法
取得指定的物件上的選擇性資訊 (從一組從傳回的堆積物件[iactivescriptprofilercontrol3:: Enumheap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md))。  
  
 您不應該釋出傳回的記憶體指派給傳回的物件。 相反地，您應該呼叫[iactivescriptprofilerheapenum:: Freeobjectandoptionalinfo 方法](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md)。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetOptionalInfo (    [in] PROFILER_HEAP_OBJECT* heapObject,    [in] ULONG celt,    [out, size_is(celt)] PROFILER_HEAP_OBJECT_OPTIONAL_INFO* optionalInfo);  
```  
  
#### <a name="parameters"></a>參數  
 `heapObject`  
 [PROFILER_HEAP_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md)要傳回的資訊。  
  
 `celt`  
 數目[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 結構](../../winscript/reference/profiler-heap-object-optional-info-structure.md)来傳回的結構。  
  
 `optionalInfo`  
 [out]陣列[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 結構](../../winscript/reference/profiler-heap-object-optional-info-structure.md)結構指定的物件。  
  
## <a name="return-value"></a>傳回值  
 HRESULT。