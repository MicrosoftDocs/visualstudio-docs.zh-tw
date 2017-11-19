---
title: "IActiveScriptAuthorProcedure::ParseProcedureText |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthorProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthorProcedure::ParseProcedureText
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9c4a1ba03a8498dbaa857dc5dbabba8914e54a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
剖析程式碼的程序，將程式碼程序的文字加入指令碼撰寫引擎，並建立`IScriptEntry`對應至程式碼的程序的物件。  
  
## <a name="syntax"></a>語法  
  
```  
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
 [in]型式參數名稱的程序的位址。 參數名稱必須以指令碼引擎的撰寫適當的分隔符號分隔。 名稱不應該在括號括住。  
  
 `pszProcedureName`  
 [in]要剖析的程序名稱的位址。  
  
 `pszItemName`  
 [in]包含項目名稱的緩衝區位址相關聯`IScriptEntry`物件。  
  
 `pszDelimiter`  
 [in]結束的指令碼區塊分隔符號的位址。 當`pszCode`剖析文字資料流，從主應用程式通常使用分隔符號 （例如兩個單引號），來偵測指令碼區塊的結尾。 如果沒有任何分隔符號來標示指令碼區塊的結尾，請設定此參數為 NULL。  
  
 `dwCookie`  
 [in]應用程式定義的值與新相關聯`IScriptEntry`物件。  
  
 `dwFlags`  
 [in]未使用。  
  
 `pdispFor`  
 [in]未使用。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 目前[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]引擎未實作這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptAuthorProcedure 介面](../../winscript/reference/iactivescriptauthorprocedure-interface.md)