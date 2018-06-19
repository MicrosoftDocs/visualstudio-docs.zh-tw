---
title: IProcessDebugManager::GetDefaultApplication |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.GetDefaultApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::GetDefaultApplication
ms.assetid: 6c991faa-ea40-4d18-a1b8-6e7d0de6dd43
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27fc46e8a5e07c4eb25c5e246db138a27e5511ae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729028"
---
# <a name="iprocessdebugmanagergetdefaultapplication"></a>IProcessDebugManager::GetDefaultApplication
傳回目前的處理序的預設應用程式物件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetDefaultApplication(  
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
 這個方法會建立新的偵錯應用程式物件，並將它加入至執行應用程式清單，如有必要。  
  
 語言引擎應該使用指定的應用程式`GetDefaultApplication`如果它們不會提供應用程式的主機上執行的方法。  
  
## <a name="see-also"></a>另請參閱  
 [IProcessDebugManager 介面](../../winscript/reference/iprocessdebugmanager-interface.md)