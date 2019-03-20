---
title: IDebugApplication::HandleBreakPoint | Microsoft Docs
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
ms.openlocfilehash: 3b05288a8863b2c555493d4a3f7ea8e2b7537d5a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146717"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
讓目前的執行緒封鎖並傳送通知之中斷點的偵錯工具 IDE。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>參數  
 `br`  
 [in]中斷的原因。  
  
 `pbra`  
 [out]偵錯工具繼續執行應用程式時要採取的動作。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 語言引擎會呼叫這個方法的叫用中斷點的執行緒內容中。 這個方法會封鎖目前的執行緒，並將中斷點通知傳送至偵錯工具 IDE。 偵錯工具會繼續執行應用程式時`pbra`參數會指定要採取的動作。  
  
> [!NOTE]
>  語言引擎可能呼叫的執行緒來執行的工作，例如列舉堆疊框架，或在中斷點期間評估運算式。  
  
 這個方法會導致`IApplicationDebugger::onHandleBreakPoint`呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [BREAKREASON 列舉](../../winscript/reference/breakreason-enumeration.md)   
 [BREAKRESUMEACTION 列舉](../../winscript/reference/breakresumeaction-enumeration.md)