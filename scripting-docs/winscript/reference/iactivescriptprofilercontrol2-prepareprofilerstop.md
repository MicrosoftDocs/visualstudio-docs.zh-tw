---
title: IActiveScriptProfilerControl2::PrepareProfilerStop |Microsoft Docs
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
ms.openlocfilehash: 086ec8b4a126c65162638afde4d8081269757e1c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089514"
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
您要停止分析在所有適用的指令碼引擎通知分析工具。 這個方法，您可以使用取得的完整呼叫堆疊如果[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]停止程式碼剖析時執行。  
  
## <a name="syntax"></a>語法  
  
```cpp
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
|`S_FALSE`|分析已停止時未執行的指令碼。|  
|`ACTIVPROF_E_PROFILER_ABSENT`|未啟用程式碼剖析。|  
  
## <a name="remarks"></a>備註  
 呼叫`IActiveScriptProfilerControl2::PrepareProfilerStop`可確保函式呼叫堆疊中的事件會傳送。 此方法，就必須停止目前的索引標籤上的任何指令碼引擎上進行分析之前呼叫。針對任何指令碼引擎，可以呼叫這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [IActiveScriptProfilerControl2 介面](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)