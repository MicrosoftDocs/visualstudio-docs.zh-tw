---
title: IMachineDebugManagerCookie::AddApplication |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManagerCookie.AddApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerCookie::AddApplication
ms.assetid: 4d5503c5-aca9-4cf7-9900-f77bf5f3263d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c71983dd5f1273679351bc45c1db2df62757d153
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977652"
---
# <a name="imachinedebugmanagercookieaddapplication"></a>IMachineDebugManagerCookie::AddApplication
新增應用程式執行的應用程式清單。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwDebugAppCookie,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pda`  
 [in]若要執行的應用程式的應用程式清單。  
  
 `dwDebugAppCookie`  
 [in]Cookie 可識別偵錯應用程式。  
  
 `pdwAppCookie`  
 [out]用來移除機器偵錯管理員的應用程式的 cookie。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會呼叫處理序偵錯管理員只要`IProcessDebugManager::AddApplication`呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [IMachineDebugManagerCookie Interface](../../winscript/reference/imachinedebugmanagercookie-interface.md)   
 [IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)