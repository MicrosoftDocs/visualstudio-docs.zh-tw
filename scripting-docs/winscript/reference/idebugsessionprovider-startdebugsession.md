---
title: IDebugSessionProvider：： StartDebugSession |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSessionProvider.StartDebugSession
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugSessionProvider::StartDebugSession
ms.assetid: 47697dfb-d4e1-492c-a14f-753e28195a76
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0fc4bdade94401d5fc7b5756eb61fddd166fe49b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574914"
---
# <a name="idebugsessionproviderstartdebugsession"></a>IDebugSessionProvider::StartDebugSession
使用指定的應用程式起始 debug 會話。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT StartDebugSession(  
   IRemoteDebugApplication*  pda  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pda`  
 在指定 debug 應用程式。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會初始化具有指定之應用程式的 debug 會話。 偵錯工具應該先呼叫 `IRemoteDebugApplication::ConnectDebugger`，然後再從這個呼叫傳回。  
  
## <a name="see-also"></a>請參閱  
 [IDebugSessionProvider 介面](../../winscript/reference/idebugsessionprovider-interface.md)   
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)