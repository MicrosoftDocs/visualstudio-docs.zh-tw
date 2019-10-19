---
title: IActiveScriptSiteDebug：： GetRootApplicationNode |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetRootApplicationNode
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetRootApplicationNode
ms.assetid: 2393f566-6b97-47c0-8041-4dd7e3b1d3a3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b19ed10178d03be0b96393ad08f1eab88ce40329
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570056"
---
# <a name="iactivescriptsitedebuggetrootapplicationnode"></a>IActiveScriptSiteDebug::GetRootApplicationNode
取得要在其下加入指令檔的應用程式節點。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetRootApplicationNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppdanRoot`  
 脫銷保存指令檔的 debug 應用程式節點。 可以是 `NULL`。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回要在其下加入指令檔的應用程式節點。 如果指令檔應該是最上層，方法可以傳回 `ppdanRoot` 的 `NULL`。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptSiteDebug 介面](../../winscript/reference/iactivescriptsitedebug-interface.md)