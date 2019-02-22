---
title: IScriptNode::GetChild |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 55cd6cf5233e850e4109128e322d3fc5bd0b1355
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086589"
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