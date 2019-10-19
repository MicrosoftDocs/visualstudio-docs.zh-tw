---
title: IMachineDebugManagerCookie：： RemoveApplication |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManagerCookie.RemoveApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerCookie::RemoveApplication
ms.assetid: af8f4a52-ec5e-48fa-87de-234d5e6528d0
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d829262245c8c14b83ce4016f103ecae68895bd9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576786"
---
# <a name="imachinedebugmanagercookieremoveapplication"></a>IMachineDebugManagerCookie::RemoveApplication
從執行中的應用程式清單中移除應用程式。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT RemoveApplication(  
   DWORD  dwDebugAppCookie,  
   DWORD  dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwDebugAppCookie`  
 在識別 debug 應用程式的 cookie。  
  
 `dwAppCookie`  
 在將應用程式新增至應用程式清單時所提供的 cookie。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 每當呼叫 `IProcessDebugManager::RemoveApplication` 時，進程 debug manager 就會呼叫這個方法。  
  
## <a name="see-also"></a>請參閱  
 [IMachineDebugManagerCookie：： AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)    
 [IMachineDebugManagerCookie 介面](../../winscript/reference/imachinedebugmanagercookie-interface.md)   
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)