---
title: "IDebugExpressionContext::GetLanguageInfo |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugExpressionContext.GetLanguageInfo
apilocation: jscript.dll
helpviewer_keywords: IDebugExpressionContext::GetLanguageInfo
ms.assetid: 35e25662-0b2a-4c3f-bce4-f01726bc04a8
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68c22d5dfcd16fb3d8f1dc3750bbfb23c4821176
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressioncontextgetlanguageinfo"></a>IDebugExpressionContext::GetLanguageInfo
傳回擁有此內容的語言名稱和 GUID。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetLanguageInfo(  
   BSTR*  pbstrLanguageName,  
   GUID*  pLanguageID  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrLanguageName`  
 [out]語言名稱。  
  
 `pLanguageID`  
 [out]語言的唯一識別碼。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回擁有此內容的語言名稱和 GUID。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugExpressionContext 介面](../../winscript/reference/idebugexpressioncontext-interface.md)