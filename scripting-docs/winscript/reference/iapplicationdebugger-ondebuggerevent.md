---
title: IApplicationDebugger：： onDebuggerEvent |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onDebuggerEvent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onDebuggerEvent
ms.assetid: 82a5faaa-1222-4bf1-8569-10439dbdf16d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f8edb2a3c39d639b5b6722707d7b6c0b57a5c19
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577858"
---
# <a name="iapplicationdebuggerondebuggerevent"></a>IApplicationDebugger::onDebuggerEvent
處理自訂應用程式事件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT onDebuggerEvent(  
   REFIID     riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>參數  
 `riid`  
 在物件的介面識別碼。  
  
 `punk`  
 在事件物件，它會執行 `riid` 所定義的介面。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|目前未執行方法。|  
  
## <a name="remarks"></a>備註  
 @No__t_0 的語義會定義完整的應用程式/偵錯工具。  
  
 這個方法允許偵錯工具模型的自訂擴充功能;目前未執行。  
  
 呼叫 `IDebugApplication::FireDebuggerEvent` 時，會呼叫這個方法。  
  
## <a name="see-also"></a>請參閱  
 [IApplicationDebugger 介面](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)