---
title: IActiveScriptAuthor::GetChars |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetChars
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetChars
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06e7a7cf276e589aaaa3c00ecab8cbf881942f82
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094324"
---
# <a name="iactivescriptauthorgetchars"></a>IActiveScriptAuthor::GetChars
傳回完成要求的完成內容的字元集。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### <a name="parameters"></a>參數  
 `fRequestedList`  
 [in]要求的完成內容中。  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|0x0001|要求的左側列舉型別。|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0x0002|要求成員完成內容。|  
|SCRIPT_CMPL_PARAM_TRIGGER|0x0003|要求的參數清單。|  
|SCRIPT_CMPL_COMMIT|0x0004|參數清單的要求完成。|  
  
 `pbstrChars`  
 [out]對應到要求的完成內容的字元。  
  
|`fRequestedList` 參數|傳回的字元|  
|--------------------------------|-------------------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|"."|  
|SCRIPT_CMPL_MEMBER_TRIGGER|"="|  
|SCRIPT_CMPL_PARAM_TRIGGER|"(,"|  
|SCRIPT_CMPL_COMMIT|"()"|  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)