---
title: "IMachineDebugManager::RemoveApplication |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IMachineDebugManager.RemoveApplication
apilocation: scrobj.dll
helpviewer_keywords: IMachineDebugManager::RemoveApplication
ms.assetid: 873509ce-e638-484a-b2a2-489a8ce7dbfe
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6ee371ded11f38b5e049e236c92292d6f662f525
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagerremoveapplication"></a>IMachineDebugManager::RemoveApplication
移除應用程式從執行的應用程式清單。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT RemoveApplication(  
   DWORD  dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwAppCookie`  
 [in]應用程式加入至應用程式清單時提供 cookie。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會呼叫處理序偵錯管理員每當`IProcessDebugManager::RemoveApplication`呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [IMachineDebugManager::AddApplication](../../winscript/reference/imachinedebugmanager-addapplication.md)   
 [IMachineDebugManager 介面](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)