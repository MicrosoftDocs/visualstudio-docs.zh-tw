---
title: IActiveScriptProfilerControl2::PrepareProfilerStop |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 78078cd874be1d7d3d169be2d3d70e65866be3fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724518"
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
通知分析工具，您要停止分析上所有適用的指令碼引擎。 使用此方法，您可以取得完整的呼叫堆疊如果[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]停止程式碼剖析時執行。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT PrepareProfilerStop();  
```  
  
#### <a name="parameters"></a>參數  
 此方法不採用任何參數。  
  
## <a name="return-value"></a>傳回值  
 會傳回 HRESULT。 可能的值如下：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|程式碼剖析無法啟動。|  
|`S_FALSE`|程式碼剖析已停止時未執行的指令碼。|  
|`ACTIVPROF_E_PROFILER_ABSENT`|未啟用程式碼剖析。|  
  
## <a name="remarks"></a>備註  
 呼叫`IActiveScriptProfilerControl2::PrepareProfilerStop`可確保傳送的事件呼叫堆疊中的函式。 這個方法沒有停止在目前的索引標籤上的任何指令碼引擎的程式碼剖析之前呼叫。方法可以呼叫的任何指令碼引擎。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [IActiveScriptProfilerControl2 介面](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)