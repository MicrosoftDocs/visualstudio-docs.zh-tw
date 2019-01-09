---
title: IScriptNode::Delete |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.Delete
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Delete
ms.assetid: 6765ff80-a9a8-40a3-a669-7fcc284c87af
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cce802cc1a6d63001cfbed020592b30a9d8dab1b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094792"
---
# <a name="iscriptnodedelete"></a>IScriptNode::Delete
刪除此物件樹狀結構。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Delete();  
```  
  
#### <a name="parameters"></a>參數  
 此方法會採用任何參數。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 在後`Delete`呼叫方法時， [IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)方法應該會指出該指令碼的節點不在使用中。  
  
## <a name="see-also"></a>另請參閱  
 [IScriptNode 介面](../../winscript/reference/iscriptnode-interface.md)