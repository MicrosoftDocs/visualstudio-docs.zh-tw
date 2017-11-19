---
title: "IDebugApplicationNode::Attach |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationNode.Attach
apilocation: pdm.dll
helpviewer_keywords: IDebugApplicationNode::Attach
ms.assetid: f4aad4ae-5bb0-4b5e-8f70-912a677f8f7a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 393186330979d464fe54bde339806a5d8335a859
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnodeattach"></a>IDebugApplicationNode::Attach
此應用程式將節點加入至指定的專案樹狀結構。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdanParent`  
 [in]要新增此應用程式節點的專案樹狀結構。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會在專案中加入此應用程式節點樹狀結構、 使用`pdanParent`做為父系。 如果`pdanParent`是`NULL`，這個應用程式節點將會是最上層節點。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)   
 [IDebugApplicationNode 介面](../../winscript/reference/idebugapplicationnode-interface.md)