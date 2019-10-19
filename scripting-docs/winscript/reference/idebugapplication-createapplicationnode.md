---
title: IDebugApplication：： CreateApplicationNode |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.CreateApplicationNode
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::CreateApplicationNode
ms.assetid: 1a1414f6-df14-4c56-b39a-8384cf16174a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13e94a561ca78781167843124a86febb3ef13da2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573164"
---
# <a name="idebugapplicationcreateapplicationnode"></a>IDebugApplication::CreateApplicationNode
建立與特定檔提供者相關聯的新應用程式節點。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CreateApplicationNode(  
   IDebugApplicationNode**  ppdanNew  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppdanNew`  
 脫銷與此檔提供者相關聯的應用程式節點。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 在附加至父節點之前，不會顯示新的應用程式節點。  
  
## <a name="see-also"></a>請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)