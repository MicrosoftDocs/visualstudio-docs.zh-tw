---
title: IScriptNode：： Alive |Microsoft Docs
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
ms.openlocfilehash: b7e0216824506ee942b42a42d5c3c4475f63f9e2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573619"
---
# <a name="iscriptnodealive"></a>IScriptNode::Alive
指出物件是否仍在作用中。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Alive();  
```  
  
#### <a name="parameters"></a>參數  
 方法不接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|[腳本] 節點仍在使用中。|  
  
## <a name="remarks"></a>備註  
 如果物件不在使用中，則元件物件模型（COM）會從封送處理 proxy 傳回錯誤，以呼叫此方法。  
  
## <a name="see-also"></a>請參閱  
 [IScriptNode 介面](../../winscript/reference/iscriptnode-interface.md)