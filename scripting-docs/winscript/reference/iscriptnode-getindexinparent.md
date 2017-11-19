---
title: "IScriptNode::GetIndexInParent |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptNode.GetIndexInParent
apilocation: scrobj.dll
helpviewer_keywords: IScriptNode::GetIndexInParent
ms.assetid: 521c1ca1-2d27-4344-bf3b-d8b53132b648
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3862a48ff4649f018eec79bf0411f23bc9f6d7bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodegetindexinparent"></a>IScriptNode::GetIndexInParent
傳回父系的子清單中的物件索引。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetIndexInParent(  
   ULONG              pisn,  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pisn`  
 [out]傳回父系的子清單中的物件索引。  
  
 如果這個方法會呼叫`IScriptNode`物件，表示網頁，這個參數會傳回 0。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IScriptNode 介面](../../winscript/reference/iscriptnode-interface.md)