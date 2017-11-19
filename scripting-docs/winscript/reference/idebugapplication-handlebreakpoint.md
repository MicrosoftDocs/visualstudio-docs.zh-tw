---
title: "IDebugApplication::HandleBreakPoint |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.HandleBreakPoint
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::HandleBreakPoint
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16b05533c566cb90529766d81fb7197dbc284664
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
會導致目前的執行緒可封鎖，並傳送通知之中斷點的 IDE 偵錯工具。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>參數  
 `br`  
 [in]中斷的原因。  
  
 `pbra`  
 [out]偵錯工具會繼續執行應用程式時要採取的動作。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 語言引擎會呼叫這個方法的叫用中斷點的執行緒內容中。 這個方法會封鎖目前的執行緒，並將中斷點通知傳送至偵錯工具 IDE。 當偵錯工具會繼續執行應用程式，`pbra`參數會指定要採取的動作。  
  
> [!NOTE]
>  語言引擎可能會被呼叫的執行緒執行工作，例如列舉堆疊框架，或在中斷點期間評估運算式。  
  
 這個方法會導致`IApplicationDebugger::onHandleBreakPoint`呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [BREAKREASON 列舉](../../winscript/reference/breakreason-enumeration.md)   
 [BREAKRESUMEACTION 列舉](../../winscript/reference/breakresumeaction-enumeration.md)