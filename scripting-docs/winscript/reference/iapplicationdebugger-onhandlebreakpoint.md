---
title: IApplicationDebugger：： onHandleBreakPoint |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onHandleBreakPoint
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onHandleBreakPoint
ms.assetid: 31adcecd-d6c1-4222-ab2c-32ec2fefb322
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3796ea1f50f0c4bcf945dbc10592c048db22757b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577834"
---
# <a name="iapplicationdebuggeronhandlebreakpoint"></a>IApplicationDebugger::onHandleBreakPoint
處理中斷點事件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT onHandleBreakPoint(  
   IRemoteDebugApplicationThread*  prpt,  
   BREAKREASON                     br,  
   IActiveScriptErrorDebug*        pError  
);  
```  
  
#### <a name="parameters"></a>參數  
 `prpt`  
 在發生中斷點的執行緒。  
  
 `br`  
 在中斷點的原因。  
  
 `pError`  
 在當 `br` 的值為 BREAKREASON_ERROR 時，所提供的執行階段錯誤資訊。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 當叫用中斷點並呼叫 `IDebugApplication::HandleBreakPoint` 時，就會呼叫這個方法。  
  
 應用程式會保持擱置，直到偵錯工具 IDE 呼叫 `IRemoteDebugApplication::ResumeFromBreakPoint` 為止。  
  
## <a name="see-also"></a>請參閱  
 [IApplicationDebugger 介面](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication：： HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)    
 [IRemoteDebugApplication：： ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)    
 [BREAKREASON 列舉](../../winscript/reference/breakreason-enumeration.md)