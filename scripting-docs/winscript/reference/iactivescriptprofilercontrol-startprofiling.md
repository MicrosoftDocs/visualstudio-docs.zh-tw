---
title: IActiveScriptProfilerControl：： StartProfiling |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.StartProfiling
apilocation:
- scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b37b60f50351496faceb97190ae0d173eba3a5f4
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983262"
---
# <a name="iactivescriptprofilercontrolstartprofiling"></a>IActiveScriptProfilerControl::StartProfiling
開始在腳本引擎上進行程式碼剖析。 腳本引擎會呼叫[CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance)來建立 profiler 物件的實例。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>參數  
 `clsidProfilerObject`  
 在要建立之 profiler 物件的類別識別碼（CLSID）。  
  
 `dwEventMask`  
 在4位元組的位元遮罩，指定事件的類型。 位是在[PROFILER_EVENT_MASK 列舉](../../winscript/reference/profiler-event-mask-enumeration.md)中定義。  
  
 `dwContext`  
 在傳遞至 profiler 物件的4位元組值。  
  
## <a name="return-value"></a>傳回值  
 傳回 HRESULT。 可能的值如下：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|方法成功。|  
|`ACTIVPROF_E_PROFILER_PRESENT`|已啟用程式碼剖析。|  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptProfilerControl 介面](../../winscript/reference/iactivescriptprofilercontrol-interface.md)