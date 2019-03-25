---
title: IScriptNode::GetChild | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetChild
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78b5c84c6ed9b3de9593f0d6ff02df93a0e9ba77
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159110"
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
傳回位於指定索引中的節點的子系。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>參數  
 `isn`  
 [in]與父系之子系的索引。  
  
 `ppsn`  
 [out]收到的指標變數的位址`IScriptNode`子執行個體的介面。  
  
 針對`IScriptNode`代表網頁的物件，此參數會傳回包含指令碼區塊的物件。  
  
 針對`IScriptEntry`指定指令碼區塊的物件，此參數傳回的物件，指定的函式。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 針對`IScriptEntry`物件，以指定的函式物件和`IScriptScriptlet`物件，這個方法會失敗，因為沒有子系項目。  
  
## <a name="see-also"></a>另請參閱  
 [IScriptNode 介面](../../winscript/reference/iscriptnode-interface.md)