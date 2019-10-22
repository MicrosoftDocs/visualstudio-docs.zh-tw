---
title: IDebugApplicationNode：： Attach |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Attach
ms.assetid: f4aad4ae-5bb0-4b5e-8f70-912a677f8f7a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30d4e189ec878def1cfd88517654955cd2d1aa12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574777"
---
# <a name="idebugapplicationnodeattach"></a>IDebugApplicationNode::Attach
將此應用程式節點加入至指定的專案樹狀結構。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdanParent`  
 在要加入此應用程式節點的專案樹狀結構。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會使用 `pdanParent` 做為父系，將此應用程式節點加入至專案樹狀結構。 如果 `NULL` `pdanParent`，此應用程式節點將會是最上層節點。  
  
## <a name="see-also"></a>請參閱  
 [IDebugApplicationNode：:D etach](../../winscript/reference/idebugapplicationnode-detach.md)    
 [IDebugApplicationNode 介面](../../winscript/reference/idebugapplicationnode-interface.md)