---
title: IDebugApplication110：： AsynchronousCallInMainThread |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::AsynchronousCallInMainThread
ms.assetid: 13b80ff0-4bed-48c1-8031-d4147b51bf6c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04c1a2962662d0046c6b9d323a287d580ee0f3e6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577397"
---
# <a name="idebugapplication110asynchronouscallinmainthread"></a>IDebugApplication110::AsynchronousCallInMainThread
在主執行緒上進行非同步呼叫。  
  
> [!IMPORTANT]
> [IDebugApplication110 介面](../../winscript/reference/idebugapplication110-interface.md)是由 PDM 11.0 和更新版本所執行。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>參數  
 `pptc`  
 要呼叫的[IDebugThreadCall 介面](../../winscript/reference/idebugthreadcall-interface.md)物件。  
  
 `dwParam1`  
 呼叫的第一個參數。  
  
 `dwParam1`  
 呼叫的第一個參數。  
  
 `dwParam2`  
 呼叫的第二個參數。  
  
 `dwParam3`  
 呼叫的第三個參數。  
  
## <a name="see-also"></a>請參閱  
 [IDebugApplication110 介面](../../winscript/reference/idebugapplication110-interface.md)