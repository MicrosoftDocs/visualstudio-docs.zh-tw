---
title: "IDebugApplicationThread110::AsynchronousCallIntoThread |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 06b3031a-4aec-4a47-afaa-04642a4c4870
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d4275d42ec102557cce12127f47a33a53c4dba6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthread110asynchronouscallintothread"></a>IDebugApplicationThread110::AsynchronousCallIntoThread
在主執行緒上進行非同步呼叫。  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 介面](../../winscript/reference/idebugapplicationthread110-interface.md)會實作由 PDM v11.0 和更新版本。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>參數  
 `pptc`  
 [IDebugThreadCall 介面](../../winscript/reference/idebugthreadcall-interface.md)物件來呼叫。  
  
 `dwParam1`  
 呼叫的第一個參數。  
  
 `dwParam1`  
 呼叫的第一個參數。  
  
 `dwParam2`  
 呼叫第二個參數。  
  
 `dwParam3`  
 第三個呼叫的參數。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplication110 介面](../../winscript/reference/idebugapplication110-interface.md)