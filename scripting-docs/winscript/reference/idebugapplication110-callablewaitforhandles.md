---
title: IDebugApplication110：： CallableWaitForHandles |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::CallableWaitForHandles
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22af0e9dcf548bbd2f0f8c179b4889d5294eb284
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575079"
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
等候任何指定的控制碼收到信號，同時允許將跨執行緒呼叫張貼到這個執行緒。 這個方法必須從偵錯工具執行緒呼叫。  
  
> [!IMPORTANT]
> [IDebugApplication110 介面](../../winscript/reference/idebugapplication110-interface.md)是由 PDM 11.0 和更新版本所執行。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
```  
  
#### <a name="parameters"></a>參數  
 `handleCount`  
 要等候的控制碼數目。  
  
 `pHandles`  
 要等候的控制碼集。  
  
 `pIndex`  
 當 HRESULT 值為 S_OK 時，會將索引放入已發出信號的控制碼 `pHandles`。  
  
## <a name="see-also"></a>請參閱  
 [IDebugApplication110 介面](../../winscript/reference/idebugapplication110-interface.md)