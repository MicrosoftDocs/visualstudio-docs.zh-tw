---
title: IScriptNode::GetParent |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: b45fc7be1a5178e952fefcd794171410d149a1f4
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090021"
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