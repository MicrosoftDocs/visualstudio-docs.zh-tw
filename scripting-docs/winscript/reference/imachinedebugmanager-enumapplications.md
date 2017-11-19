---
title: "IMachineDebugManager::EnumApplications |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IMachineDebugManager.EnumApplications
apilocation: scrobj.dll
helpviewer_keywords: IMachineDebugManager::EnumApplications
ms.assetid: 5d833db4-fd9b-4e61-bebb-130faede5a77
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1fd7ddd263aab6742e5e6a23c86f7c4480c6561a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagerenumapplications"></a>IMachineDebugManager::EnumApplications
傳回目前執行的應用程式清單的列舉值。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumApplications(  
   IEnumRemoteDebugApplications**  ppeda  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppeda`  
 [out]包含目前執行的應用程式清單的列舉值。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回目前執行的應用程式清單的列舉值。 IDE 偵錯工具會顯示，並將連接以進行偵錯的應用程式使用這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [IMachineDebugManager 介面](../../winscript/reference/imachinedebugmanager-interface.md)