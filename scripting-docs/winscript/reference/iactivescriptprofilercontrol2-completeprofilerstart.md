---
title: "IActiveScriptProfilerControl2::CompleteProfilerStart |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::CompleteProfilerStart
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5abd4ee4237991714bfe3d8ba21b083f1a1920cd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
您已經啟動上所有適用的指令碼引擎的分析通知分析工具。 使用此方法，您可以取得完整的呼叫堆疊如果[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]啟動程式碼剖析時執行。  
  
## <a name="syntax"></a>語法  
  
```  
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
|`E_OUTOFMEMORY`|因為記憶體不足狀況，無法取得呼叫堆疊。|  
  
## <a name="remarks"></a>備註  
 呼叫`IActiveScriptProfilerControl2::CompleteProfilerStart`可確保已在呼叫堆疊中的函式的事件會傳送。 這個方法沒有任何目前的索引標籤上的指令碼引擎上啟動程式碼剖析後呼叫。方法可以呼叫的任何指令碼引擎。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [IActiveScriptProfilerControl2 介面](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)