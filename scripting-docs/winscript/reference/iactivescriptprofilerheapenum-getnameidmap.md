---
title: IActiveScriptProfilerHeapEnum::GetNameIdMap | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 88514c93-850b-48d4-9a68-1e27d7411f0d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3284557bf71a038d884c1f8786755b7761770e21
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992854"
---
# <a name="iactivescriptprofilerheapenumgetnameidmap"></a>IActiveScriptProfilerHeapEnum::GetNameIdMap
傳回字串的名稱對應至[PROFILER_HEAP_OBJECT_NAME_ID 類型](../../winscript/reference/profiler-heap-object-name-id-type.md)值。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetNameIdMap (    [out, size_is(,*pcelt)] LPCWSTR* pNameList[],     [out] UINT *pcelt);  
```  
  
#### <a name="parameters"></a>參數  
 `pNameList`  
 [out]與相關聯的名稱陣列[PROFILER_HEAP_OBJECT_NAME_ID 類型](../../winscript/reference/profiler-heap-object-name-id-type.md)值。  
  
 `pcelt`  
 [out]陣列中的名稱的數目。  
  
## <a name="return-value"></a>傳回值  
 HRESULT。