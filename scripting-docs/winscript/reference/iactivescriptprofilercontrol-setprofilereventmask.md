---
title: IActiveScriptProfilerControl::SetProfilerEventMask |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.SetProfilerEventMask
apilocation:
- scrobj.dll
ms.assetid: 207e192f-e12e-4fcb-b4d8-eaee50ecb86e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b20b5410af7e48f1b9dadb937e794c1941e74df
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724848"
---
# <a name="iactivescriptprofilercontrolsetprofilereventmask"></a>IActiveScriptProfilerControl::SetProfilerEventMask
設定指定的指令碼引擎應該引發的事件類型的 4 位元組位元遮罩。  
  
## <a name="syntax"></a>語法  
  
```  
RESULT SetProfilerEventMask(  
    [in] DWORD dwEventMask);  
```  
  
#### <a name="parameters"></a>參數  
 `dwEventMask`  
 [in]4 位元組位元遮罩，指定的事件類型。 中所定義之位元[PROFILER_EVENT_MASK 列舉](../../winscript/reference/profiler-event-mask-enumeration.md)。  
  
## <a name="return-value"></a>傳回值  
 會傳回 HRESULT。 可能的值如下：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|方法成功。|  
|`ACTIVPROF_E_PROFILER_ABSENT`|未啟用程式碼剖析。|  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptProfilerControl 介面](../../winscript/reference/iactivescriptprofilercontrol-interface.md)