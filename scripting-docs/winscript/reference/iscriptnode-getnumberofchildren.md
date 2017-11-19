---
title: "IScriptNode::GetNumberOfChildren |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptNode.GetNumberOfChildren
apilocation: scrobj.dll
helpviewer_keywords: IScriptNode::GetNumberOfChildren
ms.assetid: 3451c7e9-cb50-482e-9038-6e7d7ce1ecdf
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fdb46527ca78d56b3c03a454c6194e80be19e945
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodegetnumberofchildren"></a>IScriptNode::GetNumberOfChildren
傳回的子節點數目`IScriptNode`物件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetNumberOfChildren(  
   ULONG              *pcsn  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pcsn`  
 [out]子節點數目，`IScriptNode`物件。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IScriptNode 介面](../../winscript/reference/iscriptnode-interface.md)