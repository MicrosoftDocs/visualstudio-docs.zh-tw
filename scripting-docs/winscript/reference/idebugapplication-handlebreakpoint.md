---
title: IDebugApplication：： HandleBreakPoint |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleBreakPoint
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30937817424e88f80cfa6afa8c874adfd2b2687b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574970"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
使目前線程封鎖並傳送中斷點的通知至偵錯工具 IDE。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>參數  
 `br`  
 在中斷的原因。  
  
 `pbra`  
 脫銷當偵錯工具繼續應用程式時所要採取的動作。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 語言引擎會在叫用中斷點的執行緒內容中呼叫這個方法。 這個方法會封鎖目前的執行緒，並將中斷點通知傳送至偵錯工具 IDE。 當偵錯工具繼續執行應用程式時，`pbra` 參數會指定要採取的動作。  
  
> [!NOTE]
> 語言引擎可能會由執行緒呼叫來執行工作，例如列舉堆疊框架，或在中斷點期間評估運算式。  
  
 這個方法會導致呼叫 `IApplicationDebugger::onHandleBreakPoint`。  
  
## <a name="see-also"></a>請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger：： onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)    
 [BREAKREASON 列舉](../../winscript/reference/breakreason-enumeration.md)   
 [BREAKRESUMEACTION 列舉](../../winscript/reference/breakresumeaction-enumeration.md)