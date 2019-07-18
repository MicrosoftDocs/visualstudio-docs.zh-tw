---
title: IScriptNode::GetParent |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetParent
ms.assetid: 0fb813f6-ab94-46b2-b0cf-ef5d1cd38ae4
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c990b5ba5c3d03d319e0eeced282c92cfbb5281
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786852"
---
# <a name="iscriptnodegetparent"></a>IScriptNode::GetParent
傳回`IScriptNode`物件的父系的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetParent(  
   IScriptNode       **ppsnParent  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppsnParent`  
 [out]收到的指標變數的位址`IScriptNode`父執行個體的介面。  
  
 如果類別實作`IScriptEntry`或是`IScriptScriptlet`、`IScriptNode`會傳回物件。  
  
 如果類別實作`IScriptNode`（代表網頁，） 會傳回 NULL。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IScriptNode 介面](../../winscript/reference/iscriptnode-interface.md)