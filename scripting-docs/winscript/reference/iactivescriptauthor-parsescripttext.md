---
title: "IActiveScriptAuthor::ParseScriptText |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.ParseScriptText
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::ParseScriptText
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13e81d96ae817b2117f12cb56fd59759f4c2b849
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
剖析指令碼文字、 將文字加入指令碼撰寫引擎，並建立`IScriptEntry`對應至指令碼區塊的物件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszCode`  
 [in]要剖析的指令碼文字。  
  
 `pszItemName`  
 [in]緩衝區位址，其中包含與指令碼區塊相關聯的項目名稱。  
  
 `pszDelimiter`  
 [in]結束的指令碼區塊分隔符號的位址。 當`pszCode`剖析文字資料流，從主應用程式通常使用分隔符號 （例如兩個單引號），來偵測指令碼區塊的結尾。 如果沒有任何分隔符號來識別指令碼區塊的結尾，請設定此參數為 NULL。  
  
 `dwCookie`  
 [in]應用程式定義的值與新相關聯`IScriptEntry`物件。  
  
 `dwFlags`  
 [in]未使用。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)