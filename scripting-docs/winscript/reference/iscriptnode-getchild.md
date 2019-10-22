---
title: IScriptNode：： System.windows.media.visualtreehelper.getchild |Microsoft Docs
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
ms.openlocfilehash: 27ddde527be1ea4148e4166581ab2cb1a71d15f7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573558"
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
傳回節點中位於指定索引處的子系。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>參數  
 `isn`  
 在父系中子系的索引。  
  
 `ppsn`  
 脫銷接收子實例之 `IScriptNode` 介面指標的變數位址。  
  
 對於代表網頁的 `IScriptNode` 物件，此參數會傳回包含腳本區塊的物件。  
  
 對於指定腳本區塊的 `IScriptEntry` 物件，此參數會傳回指定函數的物件。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 針對指定函式物件和 `IScriptScriptlet` 物件的 `IScriptEntry` 物件，這個方法會失敗，因為沒有子專案。  
  
## <a name="see-also"></a>請參閱  
 [IScriptNode 介面](../../winscript/reference/iscriptnode-interface.md)