---
title: "IJsDebugDataTarget 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94e158ced0da6d59bfcadeb87bf206c94a6099ad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatarget-interface"></a>IJsDebugDataTarget 介面
藉由偵錯工具提供功能來存取及變更目標偵錯工具處理序的狀態。  
  
## <a name="syntax"></a>語法  
  
```  
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[IJsDebugDataTarget::AllocateVirtualMemory 方法](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|保留和/或認可的目標處理序的虛擬位址空間中的記憶體區域。|  
|[IJsDebugDataTarget::CreateStackFrameEnumerator 方法](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|建立堆疊框架的列舉值。|  
|[IJsDebugDataTarget::FreeVirtualMemory 方法](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|釋放及/或回收的目標處理序的虛擬位址空間中的記憶體區域。|  
|[IJsDebugDataTarget::GetThreadContext 方法](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|擷取內容提供執行緒。|  
|[IJsDebugDataTarget::GetTlsValue 方法](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|正在進行偵錯的執行緒，擷取指定的 TLS 索引執行緒區域儲存區 (TLS) 插槽中的值。|  
|[IJsDebugDataTarget::ReadBSTR 方法](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|讀取偵錯目標的 BSTR。|  
|[IJsDebugDataTarget::ReadMemory 方法](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|讀取目標處理序的記憶體。|  
|[IJsDebugDataTarget::ReadNullTerminatedString 方法](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|從目標中讀取指定的字元數。|  
|[IJsDebugDataTarget::WriteMemory 方法](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|讀取目標處理序的記憶體。|  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)