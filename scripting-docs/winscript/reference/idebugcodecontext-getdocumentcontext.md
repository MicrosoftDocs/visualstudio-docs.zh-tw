---
title: IDebugCodeCoNtext：： GetDocumentCoNtext |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugCodeContext.GetDocumentContext
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugCodeContext::GetDocumentContext
ms.assetid: 9fe17b65-3a8c-4d21-9b66-0e4ff303af72
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9dc1cda6164375f3434ee562b540e85268fe4c68
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573219"
---
# <a name="idebugcodecontextgetdocumentcontext"></a>IDebugCodeContext::GetDocumentContext
傳回與此程式碼內容相關聯的檔內容。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetDocumentContext(  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppsc`  
 脫銷與此程式碼內容相關聯的檔內容。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 若為文字檔，字元位置範圍應包含整個語句的文字。 這可讓偵錯工具 IDE 反白顯示目前的來源語句。  
  
## <a name="see-also"></a>請參閱  
 [IDebugCodeContext 介面](../../winscript/reference/idebugcodecontext-interface.md)