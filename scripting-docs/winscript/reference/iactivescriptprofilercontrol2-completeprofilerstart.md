---
title: IActiveScriptProfilerControl2::CompleteProfilerStart |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::CompleteProfilerStart
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b307352a3ba6d10ec3ae434536dee82d22504d33
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091282"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
通知分析工具，您已開始分析在所有適用的指令碼引擎。 這個方法，您可以使用取得的完整呼叫堆疊如果[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]啟動程式碼剖析時執行。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>參數  
 此方法不採用任何參數。  
  
## <a name="return-value"></a>傳回值  
 會傳回 HRESULT。 可能的值如下：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|無法啟動程式碼剖析。|  
|`S_FALSE`|程式碼剖析已啟動時不執行的指令碼。|  
|`ACTIVPROF_E_PROFILER_ABSENT`|未啟用程式碼剖析。 尚未設定任何回呼。|  
|`E_OUTOFMEMORY`|無法取得呼叫堆疊，因為記憶體不足的狀況。|  
  
## <a name="remarks"></a>備註  
 呼叫`IActiveScriptProfilerControl2::CompleteProfilerStart`可確保已在呼叫堆疊中的函式的事件會傳送。 這個方法有分析上目前的索引標籤上的任何指令碼引擎啟動後呼叫。針對任何指令碼引擎，可以呼叫這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [IActiveScriptProfilerControl2 介面](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)