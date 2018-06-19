---
title: IMachineDebugManager::AddApplication |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManager.AddApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManager::AddApplication
ms.assetid: 7cd591b6-718c-4e77-acb7-a6dd147ddf57
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77c31084ccc24a6bace18f009eb8372a4f68a428
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728788"
---
# <a name="imachinedebugmanageraddapplication"></a>IMachineDebugManager::AddApplication
新增應用程式來執行應用程式清單。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pda`  
 [in]應用程式執行應用程式清單。  
  
 `pdwAppCookie`  
 [out]用來從電腦偵錯管理員移除應用程式的 cookie。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會呼叫處理序偵錯管理員每當`IProcessDebugManager::AddApplication`呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [IMachineDebugManager 介面](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IMachineDebugManager::RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)