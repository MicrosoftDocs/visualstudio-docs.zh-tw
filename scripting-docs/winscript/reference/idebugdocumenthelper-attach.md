---
title: 'Idebugdocumenthelper:: Attach |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: f0f397f70d994d0997163a06766d32c35e9b2ab7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090138"
---
# <a name="idebugdocumenthelperattach"></a>IDebugDocumentHelper::Attach
將這份文件加入至文件樹狀目錄中。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Attach(  
   IDebugDocumentHelper*  pddhParent  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pddhParent`  
 [in]本文件將會新增到文件樹狀結構。 可以是 NULL。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會將這份文件加入至文件樹狀結構、 使用`pddhParent`做為父系。 如果`pddhParent`是`NULL`，本文件將會是最上層的文件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)   
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)