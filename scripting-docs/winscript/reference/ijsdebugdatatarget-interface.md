---
title: IJsDebugDataTarget 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85c77209230abfe261c9ec0b884ad0a677cfbf07
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572459"
---
# <a name="ijsdebugdatatarget-interface"></a>IJsDebugDataTarget 介面
由偵錯工具所執行，提供存取和變更目標偵錯工具進程狀態的功能。  
  
## <a name="syntax"></a>語法  
  
```cpp
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|[屬性]|描述|  
|----------|-----------------|  
|[IJsDebugDataTarget::AllocateVirtualMemory 方法](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|保留及/或認可目標進程的虛擬位址空間內的記憶體區域。|  
|[IJsDebugDataTarget::CreateStackFrameEnumerator 方法](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|建立堆疊框架的列舉值。|  
|[IJsDebugDataTarget::FreeVirtualMemory 方法](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|釋放和（或）解除鎖定目標進程之虛擬位址空間內的記憶體區域。|  
|[IJsDebugDataTarget::GetThreadContext 方法](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|抓取指定執行緒的內容。|  
|[IJsDebugDataTarget::GetTlsValue 方法](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|對於正在進行調試的執行緒，會針對指定的 TLS 索引，抓取執行緒區域儲存區（TLS）插槽中的值。|  
|[IJsDebugDataTarget::ReadBSTR 方法](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|從 debug 目標讀取 BSTR。|  
|[IJsDebugDataTarget::ReadMemory 方法](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|讀取目標進程的記憶體。|  
|[IJsDebugDataTarget::ReadNullTerminatedString 方法](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|從目標讀取指定的字元數。|  
|[IJsDebugDataTarget::WriteMemory 方法](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|讀取目標進程的記憶體。|  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag。h  
  
## <a name="see-also"></a>請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)