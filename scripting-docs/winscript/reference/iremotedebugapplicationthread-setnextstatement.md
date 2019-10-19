---
title: IRemoteDebugApplicationThread：： SetNextStatement |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.SetNextStatement
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::SetNextStatement
ms.assetid: 356766da-f7b7-4e8d-b4f3-2ab8da0609b8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71e690d0e5b7567aabc88aabde907b67517f12aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575513"
---
# <a name="iremotedebugapplicationthreadsetnextstatement"></a>IRemoteDebugApplicationThread::SetNextStatement
強制執行在指定的框架內容中，盡可能靠近指定的程式碼內容。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pStackFrame`  
 在堆疊框架物件。 這個引數可能是 Null，表示應該使用目前的堆疊框架。  
  
 `pCodeContext`  
 在程式碼內容。 這個引數可能是 Null，表示應該使用目前的程式碼內容。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會強制執行在 `pStackFrame` 所指定的框架內容中，盡可能靠近 `pCodeContext` 所指定的程式碼內容。 這兩個引數都可能 `NULL`，代表目前的框架或內容。  
  
## <a name="see-also"></a>請參閱  
 [IRemoteDebugApplicationThread 介面](../../winscript/reference/iremotedebugapplicationthread-interface.md)