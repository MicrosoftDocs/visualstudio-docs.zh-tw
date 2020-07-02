---
title: IActiveScriptSiteDebug32：： GetApplication |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 0b82ab6cd37f789e98ca08c635011a7e04f5b871
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835624"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
傳回與這個腳本網站相關聯的 debug 應用程式物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppda`  
 脫銷與腳本網站相關聯之 debug 應用程式物件的指標。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|此方法已成功。|  
|`E_NOTIMPL`|主機不直接支援調試。|  
  
## <a name="remarks"></a>備註  
 `GetApplication`方法提供一種方式，讓智慧型主機定義每個腳本所屬的應用程式物件。 腳本引擎應該嘗試呼叫這個方法來取得其包含的應用程式，並 `IProcessDebugManager::GetDefaultApplication` 在發生失敗時進行操作。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSiteDebug32 介面](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)