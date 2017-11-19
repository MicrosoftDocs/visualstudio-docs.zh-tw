---
title: "IScriptNode::GetChild |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptNode.GetChild
apilocation: scrobj.dll
helpviewer_keywords: IScriptNode::GetChild
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d127b1b8a8db0c6d272e50d33b523fbe182a9e21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
傳回位於指定索引的節點中的子系。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>參數  
 `isn`  
 [in]與父系的子系的索引。  
  
 `ppsn`  
 [out]收到的指標變數的位址`IScriptNode`子執行個體的介面。  
  
 如`IScriptNode`代表網頁的物件，這個參數會傳回包含指令碼區塊的物件。  
  
 如`IScriptEntry`指定指令碼區塊的物件，這個參數會傳回指定的函式的物件。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 如`IScriptEntry`物件，以指定的函式物件和`IScriptScriptlet`物件，這個方法會失敗，因為沒有子系的項目。  
  
## <a name="see-also"></a>另請參閱  
 [IScriptNode 介面](../../winscript/reference/iscriptnode-interface.md)