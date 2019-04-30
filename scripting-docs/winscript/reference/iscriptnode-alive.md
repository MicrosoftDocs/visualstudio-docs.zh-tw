---
title: IScriptNode::Alive |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.Alive
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Alive
ms.assetid: d2755c83-e9b9-4c0a-acb7-25b554fc9fe8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da0a55d26b5ab643670ba7ed51e576eeb89d8b98
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787169"
---
# <a name="iscriptnodealive"></a>IScriptNode::Alive
指出物件是否仍在作用中。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Alive();  
```  
  
#### <a name="parameters"></a>參數  
 此方法會採用任何參數。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|指令碼的節點是仍在作用中。|  
  
## <a name="remarks"></a>備註  
 如果物件不是作用中，元件物件模型 (COM) 會傳回錯誤，從針對至這個方法的呼叫封送處理的 proxy。  
  
## <a name="see-also"></a>另請參閱  
 [IScriptNode 介面](../../winscript/reference/iscriptnode-interface.md)