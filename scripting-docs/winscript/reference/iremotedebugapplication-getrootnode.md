---
title: 'Iremotedebugapplication:: Getrootnode |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.GetRootNode
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::GetRootNode
ms.assetid: 6c043aba-1dc5-41de-9711-96cde5e040f6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75b398ddac53f2633cbc090f5d49574bd4d94d36
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097769"
---
# <a name="iremotedebugapplicationgetrootnode"></a>IRemoteDebugApplication::GetRootNode
傳回在其下加入應用程式相關聯的所有節點的應用程式節點。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetRootNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppdanRoot`  
 [out]偵錯應用程式] 節點下加入應用程式相關聯的所有節點。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回在其下加入應用程式相關聯的所有節點的應用程式節點。  
  
## <a name="see-also"></a>另請參閱  
 [IRemoteDebugApplication 介面](../../winscript/reference/iremotedebugapplication-interface.md)