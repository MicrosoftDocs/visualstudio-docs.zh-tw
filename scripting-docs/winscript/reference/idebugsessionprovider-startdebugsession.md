---
title: "IDebugSessionProvider::StartDebugSession |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugSessionProvider.StartDebugSession
apilocation: scrobj.dll
helpviewer_keywords: IDebugSessionProvider::StartDebugSession
ms.assetid: 47697dfb-d4e1-492c-a14f-753e28195a76
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e93d3bd48a544d5bb446e1bff102268a7624e85
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsessionproviderstartdebugsession"></a>IDebugSessionProvider::StartDebugSession
初始化具有指定的應用程式偵錯工作階段。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT StartDebugSession(  
   IRemoteDebugApplication*  pda  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pda`  
 [in]指定偵錯應用程式。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會起始與指定的應用程式的偵錯工作階段。 偵錯工具應該呼叫`IRemoteDebugApplication::ConnectDebugger`傳回從這個呼叫之前。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugSessionProvider 介面](../../winscript/reference/idebugsessionprovider-interface.md)   
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)