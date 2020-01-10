---
title: IActiveScriptProfilerControl2：:P repareProfilerStop |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::PrepareProfilerStop
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24d4d73e0263882ad028ea66d3fac5e24f3af9ba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571438"
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
通知分析工具您即將停止所有適用的腳本引擎上的程式碼剖析。 藉由使用這個方法，您可以在停止分析時，取得完整的呼叫堆疊（如果 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 正在執行）。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT PrepareProfilerStop();  
```  
  
#### <a name="parameters"></a>參數  
 方法不接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 傳回 HRESULT。 可能的值如下：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|無法啟動程式碼剖析。|  
|`S_FALSE`|腳本未執行時，程式碼剖析已停止。|  
|`ACTIVPROF_E_PROFILER_ABSENT`|未啟用程式碼剖析。|  
  
## <a name="remarks"></a>備註  
 呼叫 `IActiveScriptProfilerControl2::PrepareProfilerStop` 可確保呼叫堆疊中函式的事件會被傳送。 在您于目前索引標籤上的任何腳本引擎上停止分析之前，必須先呼叫這個方法。可以針對任何腳本引擎呼叫方法。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptProfilerControl2：： CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [IActiveScriptProfilerControl2 介面](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)