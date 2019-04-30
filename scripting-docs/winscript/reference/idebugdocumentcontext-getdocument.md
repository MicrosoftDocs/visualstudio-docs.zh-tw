---
title: IDebugDocumentContext::GetDocument |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentContext.GetDocument
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentContext::GetDocument
ms.assetid: 32db2fea-4938-4644-b39a-8fae05960d1d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9bfcc5b3e2d2e197619f9bc4ec19b55c9eaf1d2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974432"
---
# <a name="idebugdocumentcontextgetdocument"></a>IDebugDocumentContext::GetDocument
傳回包含此內容的文件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetDocument(  
   IDebugDocument**  ppsd  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppsd`  
 [out]包含此內容的文件。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 `GetDocument`方法會傳回包含此內容的文件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentContext 介面](../../winscript/reference/idebugdocumentcontext-interface.md)