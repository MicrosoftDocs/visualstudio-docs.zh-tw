---
title: "IActiveScriptSiteDebug32::GetDocumentContextFromPosition |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 71136a1b3cb136cbc0a97cf39f59f1f4e950048b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
語言引擎用於委派`IDebugCodeContext::GetSourceContext`。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwSourceContext`  
 [in]來源內容提供給`ParseScriptText`或`AddScriptlet`。  
  
 `uCharacterOffset`  
 [in]字元相對於指令碼區塊或程式碼片段的開始位移。  
  
 `uNumChars`  
 [in]在此內容中的字元數。  
  
 `ppsc`  
 [out]對應至這個字元位置範圍的文件內容。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 語言引擎使用這個方法來委派`IDebugCodeContext::GetSourceContext`。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSiteDebug32 介面](../../winscript/reference/iactivescriptsitedebug32-interface.md)