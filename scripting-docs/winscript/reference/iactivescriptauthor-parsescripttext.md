---
title: IActiveScriptAuthor：:P arseScriptText |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::ParseScriptText
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 90d5ab0fa700ed29b5fb37b1c48617cedec871b9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576143"
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
剖析腳本文字、將文字新增至腳本撰寫引擎，並建立與腳本區塊對應的 `IScriptEntry` 物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
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
 在要剖析的腳本文字。  
  
 `pszItemName`  
 在包含與腳本區塊相關聯之專案名稱的緩衝區位址。  
  
 `pszDelimiter`  
 在結束腳本區塊分隔符號的位址。 從文字的資料流程剖析 `pszCode` 時，主機通常會使用分隔符號（例如兩個單引號）來偵測腳本區塊的結尾。 如果沒有用來識別腳本區塊結尾的分隔符號，請將此參數設為 Null。  
  
 `dwCookie`  
 在與新的 `IScriptEntry` 物件相關聯的應用程式定義值。  
  
 `dwFlags`  
 在未使用。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)