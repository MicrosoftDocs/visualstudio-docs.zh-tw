---
title: IDebugDocumentHelper：： AddDBCSText |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddDBCSText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddDBCSText
ms.assetid: 5e5011b2-bbb4-491b-9a11-eb2846be44aa
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71d0b7816a0b8801c5fb4eaab9cf7808a3f3bbfe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577065"
---
# <a name="idebugdocumenthelperadddbcstext"></a>IDebugDocumentHelper::AddDBCSText
將 DBCS 字串附加到本檔的結尾。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT AddDBCSText(  
   LPCSTR  pszText  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszText`  
 在包含文字之以 null 終止之字串的指標。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|方法無法加入這些字元。|  
  
## <a name="remarks"></a>備註  
 這個方法會產生 `IDebugDocumentTextEvents` 通知。  
  
> [!NOTE]
> 如果在呼叫 `IDebugDocumentHelper::AddDeferredText` 之後呼叫這個方法，則會傳回 `E_FAIL`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper：： AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [IDebugDocumentTextEvents 介面](../../winscript/reference/idebugdocumenttextevents-interface.md)