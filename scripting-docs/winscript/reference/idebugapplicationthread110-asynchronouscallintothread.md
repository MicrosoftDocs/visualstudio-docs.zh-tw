---
title: IDebugApplicationThread110::AsynchronousCallIntoThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 06b3031a-4aec-4a47-afaa-04642a4c4870
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2392d34a4971389b293e44a6223c2159d6d6a9cb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345847"
---
# <a name="idebugapplicationthread110asynchronouscallintothread"></a>IDebugApplicationThread110::AsynchronousCallIntoThread
在主執行緒上進行非同步呼叫。  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 介面](../../winscript/reference/idebugapplicationthread110-interface.md)是實作由 PDM v11.0 和更新版本。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>參數  
 `pptc`  
 [IDebugThreadCall 介面](../../winscript/reference/idebugthreadcall-interface.md)呼叫的物件。  
  
 `dwParam1`  
 呼叫第一個參數。  
  
 `dwParam1`  
 呼叫第一個參數。  
  
 `dwParam2`  
 呼叫第二個參數。  
  
 `dwParam3`  
 呼叫第三個參數。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplication110 介面](../../winscript/reference/idebugapplication110-interface.md)