---
title: IActiveScriptSiteDebug32::GetApplication |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: c71e33445db7745f71e374c586d079a9665776b2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087893"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
傳回與這個指令碼網站相關聯的偵錯應用程式物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppda`  
 [out]指令碼網站相關聯的偵錯應用程式物件的指標。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|主機不直接支援偵錯。|  
  
## <a name="remarks"></a>備註  
 `GetApplication`方法可讓智慧主機用來定義每個指令碼所屬的應用程式物件。 指令碼引擎應該嘗試呼叫這個方法來取得其包含的應用程式，並以`IProcessDebugManager::GetDefaultApplication`如果此作業失敗。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSiteDebug32 介面](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)