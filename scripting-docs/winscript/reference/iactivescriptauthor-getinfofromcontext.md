---
title: IActiveScriptAuthor::GetInfoFromContext | Microsoft Docs
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
ms.openlocfilehash: e4fe885e116019608dd8d748c3cbdaff5d31dd2a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154409"
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
傳回類型的程式碼區塊中的資訊和錨點指定的字元位置。 IntelliSense、 全域清單和參數提示，這會提供成員的資訊。  
  
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
 [in]用來產生資訊結果的程式碼區塊字串的位址。  
  
 `cchCode`  
 [in]程式碼區塊的長度。  
  
 `ichCurrentPosition`  
 [in]相對於開頭的字元位置的區塊。  
  
 `dwListTypesRequested`  
 [in]要求清單的型別。 可以是下列值的組合：  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|沒有清單中。|  
|SCRIPT_CMPL_MEMBERLIST|0x0001|成員的清單。|  
|SCRIPT_CMPL_ENUMLIST|0x0002|列舉清單。|  
|SCRIPT_CMPL_PARAMLIST|0x0004|呼叫方法參數清單。|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|全域清單。|  
  
 SCRIPT_CMPL_GLOBALLIST 型別會被視為預設的完成項目，可以使用其他的完成項目中的 OR 運算子結合。 第一次撰寫引擎的指令碼會嘗試填入其他完成清單項目型別資訊。 如果失敗，SCRIPT_CMPL_GLOBALLIST 引擎將會填入。  
  
 `pdwListTypesProvided`  
 [out]提供清單型別。  
  
 `pichListAnchorPosition`  
 [out]包含目前位置的內容的起始索引。 起始索引是以相對於該區塊的開頭。  
  
 這會填入時才`dwListTypesRequested`包括 SCRIPT_CMPL_MEMBERLIST、 SCRIPT_CMPL_ENUMLIST 或 SCRIPT_CMPL_GLOBALLIST。 對於其他要求的清單型別，結果是未定義。  
  
 `pichFuncAnchorPosition`  
 [out]函式呼叫，其中包含目前位置的起始索引。 起始索引是以相對於該區塊的開頭。  
  
 以及只包含目前位置的內容是函式呼叫時，才會填入這`dwListTypesRequested`包含 SCRIPT_CMPL_PARAMLIST。 否則，結果就是未定義。  
  
 `pmemid`  
 [out]函式中的型別所定義 MEMBERID `IProvideMultipleClassInfo``ppunk` out 參數。  
  
 這會填入時才`dwListTypesRequested`包含 SCRIPT_CMPL_PARAMLIST。  
  
 `piCurrentParameter`  
 [out]包含目前位置的參數索引。 如果目前位置位於函式名稱，則傳回-1。  
  
 `piCurrentParameter`會填入值時，才`dwListTypesRequested`包含 SCRIPT_CMPL_PARAMLIST。  
  
 `ppunk`  
 型別資訊，所提供的形式`IProvideMultipleClassInfo`物件。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [IProvideMultipleClassInfo 介面](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo)   
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)