---
title: IActiveScriptAuthorProcedure：:P arseProcedureText |Microsoft Docs
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
ms.openlocfilehash: 11a34843f30274ec78f1652c5ed5cd4dbcf2884a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572825"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
剖析程式碼程式、將程式碼程式的文字新增至腳本撰寫引擎，並建立對應至程式碼程式的 `IScriptEntry` 物件。  
  
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
 在要剖析的腳本文字。  
  
 `pszFormalParams`  
 在程式正式參數名稱的位址。 參數名稱必須以腳本撰寫引擎的適當分隔符號分隔。 名稱不應括在括弧中。  
  
 `pszProcedureName`  
 在要剖析之程式名稱的位址。  
  
 `pszItemName`  
 在包含與 `IScriptEntry` 物件相關聯之專案名稱的緩衝區位址。  
  
 `pszDelimiter`  
 在結束腳本區塊分隔符號的位址。 從文字的資料流程剖析 `pszCode` 時，主機通常會使用分隔符號（例如兩個單引號）來偵測腳本區塊的結尾。 如果沒有分隔符號可標示腳本區塊的結尾，請將此參數設定為 Null。  
  
 `dwCookie`  
 在與新的 `IScriptEntry` 物件相關聯的應用程式定義值。  
  
 `dwFlags`  
 在未使用。  
  
 `pdispFor`  
 在未使用。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 目前的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 引擎不會執行此方法。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptAuthorProcedure 介面](../../winscript/reference/iactivescriptauthorprocedure-interface.md)