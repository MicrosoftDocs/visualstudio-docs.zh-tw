---
title: IDebugEngine3::SetEngineGuid | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine3::SetEngineGuid
helpviewer_keywords:
- IDebugEngine3::SetEngineGuid
ms.assetid: 8bdfa05d-feb7-4d98-abac-77825a04c50f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b4b74db445d03f2cb407e74a1a3f9aef4d4e529c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54988879"
---
# <a name="idebugengine3setengineguid"></a>IDebugEngine3::SetEngineGuid
這個方法會設定偵錯引擎 (DE) `GUID`。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetEngineGuid(  
   GUID* guidEngine  
);  
```  
  
```  
[C#]  
int SetEngineGuid(  
   ref Guid guidEngine  
);  
```  
  
#### <a name="parameters"></a>參數  
 `guidEngine`  
 [in]`GUID`的引擎。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`，否則會傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)