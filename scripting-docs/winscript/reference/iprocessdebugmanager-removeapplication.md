---
title: "IProcessDebugManager::RemoveApplication |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IProcessDebugManager.RemoveApplication
apilocation: pdm.dll
helpviewer_keywords: IProcessDebugManager::RemoveApplication
ms.assetid: 334e869d-81ae-4d30-9e89-89763ad4f184
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b8d95be6227f192596e174095744a4e0247e0c37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iprocessdebugmanagerremoveapplication"></a>IProcessDebugManager::RemoveApplication
移除應用程式從執行的應用程式清單。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT RemoveApplication(  
   DWORD  dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwAppCookie`  
 [in]所提供的 cookie`IProcessDebugManager::AddApplication`當應用程式加入至應用程式清單。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會移除應用程式從執行的應用程式清單。  
  
## <a name="see-also"></a>另請參閱  
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)   
 [IProcessDebugManager 介面](../../winscript/reference/iprocessdebugmanager-interface.md)