---
title: "IProcessDebugManager::CreateApplication |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IProcessDebugManager.CreateApplication
apilocation: pdm.dll
helpviewer_keywords: IProcessDebugManager::CreateApplication
ms.assetid: d6b646f2-8af0-445c-ae7e-a9772042b3a1
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a051462f32acae238ca5843e283fe6001ec43fc1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iprocessdebugmanagercreateapplication"></a>IProcessDebugManager::CreateApplication
建立新的偵錯應用程式物件為此應用程式。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppda`  
 [out]此應用程式偵錯應用程式物件。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法所建立的物件沒有名稱，並不會加入至執行的應用程式清單。 使用`IProcessDebugManager::AddApplication`加入偵錯應用程式到應用程式清單。  
  
## <a name="see-also"></a>另請參閱  
 [IProcessDebugManager 介面](../../winscript/reference/iprocessdebugmanager-interface.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)