---
title: "IDebugApplicationNode::GetParent |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationNode.GetParent
apilocation: pdm.dll
helpviewer_keywords: IDebugApplicationNode::GetParent
ms.assetid: 88ba3a53-0cd7-4e1f-8558-79c20ac76cc9
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 23dbc8b4dc0c12a25349ddaf7d8fd711df0a9f4b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnodegetparent"></a>IDebugApplicationNode::GetParent
傳回這個應用程式節點的父節點。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetParent(  
   IDebugApplicationNode**  pprddp  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pprddp`  
 [out]此應用程式節點的父應用程式節點。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回此應用程式節點的父節點。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplicationNode 介面](../../winscript/reference/idebugapplicationnode-interface.md)