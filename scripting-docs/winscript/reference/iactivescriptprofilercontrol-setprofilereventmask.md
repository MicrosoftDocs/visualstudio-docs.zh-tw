---
title: IActiveScriptProfilerControl：： SetProfilerEventMask |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: a4162cf2e5325bfb41bce9c3a47a52b1b36d74f2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571587"
---
# <a name="iactivescriptprofilercontrolsetprofilereventmask"></a>IActiveScriptProfilerControl::SetProfilerEventMask
設定4個位元組的位元遮罩，指定腳本引擎應該引發的事件種類。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SetProfilerEventMask(  
    [in] DWORD dwEventMask);  
```  
  
#### <a name="parameters"></a>參數  
 `dwEventMask`  
 在4位元組的位元遮罩，指定事件的類型。 位是在[PROFILER_EVENT_MASK 列舉](../../winscript/reference/profiler-event-mask-enumeration.md)中定義。  
  
## <a name="return-value"></a>傳回值  
 傳回 HRESULT。 可能的值如下：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|方法成功。|  
|`ACTIVPROF_E_PROFILER_ABSENT`|未啟用程式碼剖析。|  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptProfilerControl 介面](../../winscript/reference/iactivescriptprofilercontrol-interface.md)