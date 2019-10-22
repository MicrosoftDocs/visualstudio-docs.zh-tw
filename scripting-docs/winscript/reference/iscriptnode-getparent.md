---
title: IScriptNode：： GetParent |Microsoft Docs
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
ms.openlocfilehash: 58ef5f88f4404d57a7edad3590fba1d2614faec6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572564"
---
# <a name="iscriptnodegetparent"></a>IScriptNode::GetParent
傳回物件的父代 `IScriptNode` 物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetParent(  
   IScriptNode       **ppsnParent  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppsnParent`  
 脫銷接收父實例之 `IScriptNode` 介面指標的變數位址。  
  
 如果類別會執行 `IScriptEntry` 或 `IScriptScriptlet`，則會傳回 `IScriptNode` 物件。  
  
 如果類別會執行 `IScriptNode` （代表網頁），則會傳回 Null。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [IScriptNode 介面](../../winscript/reference/iscriptnode-interface.md)