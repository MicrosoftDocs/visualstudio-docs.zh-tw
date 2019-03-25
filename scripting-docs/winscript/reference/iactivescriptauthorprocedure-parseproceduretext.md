---
title: IActiveScriptAuthorProcedure::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthorProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthorProcedure::ParseProcedureText
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c513b105a483d0f80510dff9c91fa2c3f09e0523
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149376"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
剖析的程式碼程序，將程式碼程序的文字加入指令碼撰寫引擎，並建立`IScriptEntry`對應至程式碼程序的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszCode`  
 [in]要剖析的指令碼文字。  
  
 `pszFormalParams`  
 [in]此程序的型式參數名稱的位址。 參數名稱必須以撰寫引擎的指令碼的適當分隔符號分隔。 名稱不應該用括號括住。  
  
 `pszProcedureName`  
 [in]要剖析的程序名稱的位址。  
  
 `pszItemName`  
 [in]包含的項目名稱的緩衝區位址相關聯`IScriptEntry`物件。  
  
 `pszDelimiter`  
 [in]End 的指令碼區塊分隔符號的位址。 當`pszCode`剖析文字資料流，從主應用程式通常會使用分隔符號 （例如兩個單引號），來偵測指令碼區塊的結尾。 如果沒有任何分隔符號來標示指令碼區塊的結尾，請設定此參數為 NULL。  
  
 `dwCookie`  
 [in]應用程式定義的值與新相關聯`IScriptEntry`物件。  
  
 `dwFlags`  
 [in]不使用。  
  
 `pdispFor`  
 [in]不使用。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 目前[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]引擎不會實作這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptAuthorProcedure 介面](../../winscript/reference/iactivescriptauthorprocedure-interface.md)