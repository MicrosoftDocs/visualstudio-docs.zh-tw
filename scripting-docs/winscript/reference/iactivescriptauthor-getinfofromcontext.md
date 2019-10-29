---
title: IActiveScriptAuthor：： GetInfoFromCoNtext |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetInfoFromContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetInfoFromContext
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b8b9ad4677d580d495c72866be57712476d6a9c7
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985330"
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
傳回程序代碼區塊中指定字元的類型資訊和錨點位置。 這會提供成員 IntelliSense、全域清單和參數提示的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetInfoFromContext(  
   LPCOLESTR  pszCode,  
   ULONG      cchCode,  
   ULONG      ichCurrentPosition,  
   DWORD      dwListTypesRequested,  
   DWORD      *pdwListTypesProvided,  
   ULONG      *pichListAnchorPosition,  
   ULONG      *pichFuncAnchorPosition,  
   MEMBERID   *pmemid,  
   LONG       *piCurrentParameter,  
   IUnknown   **ppunk  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszCode`  
 在用來產生資訊結果之程式碼區塊字串的位址。  
  
 `cchCode`  
 在程式碼區塊的長度。  
  
 `ichCurrentPosition`  
 在相對於區塊開頭的字元位置。  
  
 `dwListTypesRequested`  
 在要求的清單類型。 可以是下列值的組合：  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|無清單。|  
|SCRIPT_CMPL_MEMBERLIST|0x0001|成員清單。|  
|SCRIPT_CMPL_ENUMLIST|0x0002|列舉清單。|  
|SCRIPT_CMPL_PARAMLIST|0x0004|呼叫方法參數清單。|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|全域清單。|  
  
 SCRIPT_CMPL_GLOBALLIST 類型會被視為預設的完成專案，可以使用 OR 運算子與其他完成專案結合。 腳本撰寫引擎會先嘗試填入其他完成清單專案的類型資訊。 如果失敗，引擎就會填入 SCRIPT_CMPL_GLOBALLIST。  
  
 `pdwListTypesProvided`  
 脫銷提供的清單類型。  
  
 `pichListAnchorPosition`  
 脫銷包含目前位置之內容的起始索引。 開始索引是相對於區塊的開頭。  
  
 只有當 `dwListTypesRequested` 包含 SCRIPT_CMPL_MEMBERLIST、SCRIPT_CMPL_ENUMLIST 或 SCRIPT_CMPL_GLOBALLIST 時，才會填入此內容。 若為其他要求的清單類型，則結果為未定義。  
  
 `pichFuncAnchorPosition`  
 脫銷包含目前位置之函式呼叫的起始索引。 開始索引是相對於區塊的開頭。  
  
 只有當包含目前位置的內容是函式呼叫，以及當 `dwListTypesRequested` 包含 SCRIPT_CMPL_PARAMLIST 時，才會填入此。 否則，結果會是未定義的。  
  
 `pmemid`  
 脫銷函數的 MEMBERID，如 `IProvideMultipleClassInfo``ppunk` out 參數中的類型所定義。  
  
 只有在 `dwListTypesRequested` 包含 SCRIPT_CMPL_PARAMLIST 時，才會填入此內容。  
  
 `piCurrentParameter`  
 脫銷包含目前位置之參數的索引。 如果目前的位置是在函式名稱上，則會傳回-1。  
  
 只有在 `dwListTypesRequested` 包含 SCRIPT_CMPL_PARAMLIST 時，才會填入 `piCurrentParameter` 值。  
  
 `ppunk`  
 型別資訊，以 `IProvideMultipleClassInfo` 物件的形式提供。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [IProvideMultipleClassInfo 介面](/dotnet/api/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo)   
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)