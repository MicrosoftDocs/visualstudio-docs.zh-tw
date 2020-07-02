---
title: IActiveScriptSiteDebug32：： GetDocumentCoNtextFromPosition |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: b43b16f46cc62b6c70460d79c194b5e0d2cfede0
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835273"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
供語言引擎用來委派 `IDebugCodeContext::GetSourceContext` 。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwSourceContext`  
 在提供給或的來源內容 `ParseScriptText` `AddScriptlet` 。  
  
 `uCharacterOffset`  
 在相對於腳本區塊或程式碼片段開頭的字元位移。  
  
 `uNumChars`  
 在此內容中的字元數。  
  
 `ppsc`  
 脫銷對應至這個字元位置範圍的檔內容。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|此方法已成功。|  
  
## <a name="remarks"></a>備註  
 語言引擎會使用這個方法來委派 `IDebugCodeContext::GetSourceContext` 。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSiteDebug32 介面](../../winscript/reference/iactivescriptsitedebug32-interface.md)