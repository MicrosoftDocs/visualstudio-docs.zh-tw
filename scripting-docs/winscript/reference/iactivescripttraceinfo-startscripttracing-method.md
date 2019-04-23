---
title: 'Iactivescripttraceinfo:: Startscripttracing 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b87971e1fd2e484aa54ff4de56ee56e00b19b1e6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60101011"
---
# <a name="iactivescripttraceinfostartscripttracing-method"></a>IActiveScriptTraceInfo::StartScriptTracing 方法
啟動指令碼追蹤。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT StartScriptTracing(     [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,     [in] GUID guidContextID );   
```  
  
#### <a name="parameters"></a>參數  
 `pSiteTraceInfo`  
 主機的 IActiveScriptSiteTraceInfo 指標。  
  
 `guidContextId`  
 內容的 GUID。  
  
## <a name="return-value"></a>傳回值  
 可能的傳回值，這個方法，如下所示：  
  
1. S_OK:成功。  
  
2. E_POINTER:`pSiteTraceInfo`為 NULL 指標。  
  
3. E_NOTIMPL:未實作。