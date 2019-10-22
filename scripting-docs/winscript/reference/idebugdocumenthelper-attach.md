---
title: IDebugDocumentHelper：： Attach |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Attach
ms.assetid: 834f23a9-716d-44df-b23c-d1bf6da60e79
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3400a5bf6cd3e4a9726fdf4b2f20bbf43b9fc989
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577025"
---
# <a name="idebugdocumenthelperattach"></a>IDebugDocumentHelper::Attach
將這份檔加入檔樹狀結構中。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Attach(  
   IDebugDocumentHelper*  pddhParent  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pddhParent`  
 在將加入此檔的檔樹狀結構。 可能是 Null。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會使用 `pddhParent` 做為父系，將此檔加入檔樹狀結構中。 如果 `pddhParent` 是 `NULL`，這份檔將會是最上層檔。  
  
## <a name="see-also"></a>請參閱  
 [IDebugDocumentHelper：:D etach](../../winscript/reference/idebugdocumenthelper-detach.md)    
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)