---
title: IScriptNode：： GetIndexInParent |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetIndexInParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetIndexInParent
ms.assetid: 521c1ca1-2d27-4344-bf3b-d8b53132b648
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9251f65414a5ebd48ce56dae6a7dbfeec4e514e3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575036"
---
# <a name="iscriptnodegetindexinparent"></a>IScriptNode::GetIndexInParent
傳回父項的子清單中物件的索引。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetIndexInParent(  
   ULONG              pisn,  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pisn`  
 脫銷傳回父項的子清單中物件的索引。  
  
 如果這個方法是由代表網頁的 `IScriptNode` 物件所呼叫，此參數會傳回0。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [IScriptNode 介面](../../winscript/reference/iscriptnode-interface.md)