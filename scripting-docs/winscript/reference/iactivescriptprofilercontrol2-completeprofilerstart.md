---
title: IActiveScriptProfilerControl2：： CompleteProfilerStart |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: f0230ecb480792b5b24b7375f5b95926735d0a61
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571564"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
通知分析工具您已開始對所有適用的腳本引擎進行程式碼剖析。 藉由使用這個方法，您可以在開始分析時，取得完整的呼叫堆疊（如果 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 正在執行）。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>參數  
 方法不接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 傳回 HRESULT。 可能的值如下：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|無法啟動程式碼剖析。|  
|`S_FALSE`|腳本未執行時，已開始分析。|  
|`ACTIVPROF_E_PROFILER_ABSENT`|未啟用程式碼剖析。 未設定回呼。|  
|`E_OUTOFMEMORY`|無法取得呼叫堆疊，因為發生記憶體不足的狀況。|  
  
## <a name="remarks"></a>備註  
 呼叫 `IActiveScriptProfilerControl2::CompleteProfilerStart` 可確保已在呼叫堆疊中的函式的事件會被傳送。 當分析程式在目前索引標籤上的任何腳本引擎上啟動之後，就必須呼叫這個方法。可以針對任何腳本引擎呼叫方法。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptProfilerControl2：:P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [IActiveScriptProfilerControl2 介面](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)